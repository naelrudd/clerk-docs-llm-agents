# Rotate IdP signing certificates

A Security Assertion Markup Language (SAML) identity provider (IdP) signs every single sign-on (SSO) response it sends to Clerk with a private key. Clerk verifies that signature with the matching certificate stored on the enterprise connection. IdPs rotate their keys periodically, and most of them publish the next certificate ahead of the switch so that service providers (SPs) can start trusting it early.

A SAML enterprise connection trusts up to **five signing certificates** at once. During a sign-in, Clerk accepts a response signed with any currently valid certificate in the list. This lets you add the next certificate before the IdP switches keys and remove the old one afterward, without interrupting sign-ins.

## How certificates are stored

Each connection stores an ordered list of certificates:

- **All certificates are trusted.** When Clerk verifies a response, it accepts a signature from any certificate in the list that is currently valid, so the order doesn't affect which sign-ins succeed.
- **The first certificate is the primary.** It's the one returned in the connection's `idp_certificate` field, which older integrations still read. When you save the list, Clerk moves the first currently valid certificate to the front. If none is valid, it keeps the submitted order.
- **Updating certificates replaces the whole list.** Every way to update certificates sends the complete set, so the connection ends up with exactly the certificates you listed, down to a single one.
- **Expiry is read from the certificate.** Clerk stores each certificate's validity window and shows its expiration date alongside the certificate. An expired certificate stays in the list until you remove it; Clerk keeps rejecting responses signed with it.

> A connection must keep at least **one certificate** while it's active.

## Rotate a certificate without downtime

Most IdPs publish their next signing certificate in their metadata or admin console before they start signing with it. Rotate the IdP's signing certificate in three steps:

1. ### Add the new certificate

   Use one of the [certificate management methods](#manage-certificates) to add the IdP's next certificate, and keep the current one in place. Both are now trusted, so sign-ins keep working whichever key the IdP uses.
2. ### Let the IdP switch keys

   When the IdP starts signing with the new key, nothing changes on the Clerk side. If the IdP rolls back to the old key, that still works too.
3. ### Remove the old certificate

   Once the IdP no longer signs with the old key, [remove its certificate](#manage-certificates). That's also how you revoke a leaked or retired key: remove its certificate from the list.

If the IdP already switched keys and sign-ins are failing, add its new certificate to the list and save the connection. You can remove the old certificate afterward.

> If you use IdP metadata to manage certificates, Clerk doesn't poll it for updates. To refresh the certificates, resubmit the metadata URL or upload the updated metadata file. This replaces the connection's certificate list, removing any manually added certificates that aren't in the metadata. If the IdP still signs with one of those certificates, sign-ins can fail.

## Manage certificates

There are three ways to manage a connection's certificates:

- [In the Clerk Dashboard](#in-the-clerk-dashboard)
- [From `<OrganizationProfile />`](#from-organizationprofile), if your application uses [self-serve SSO](https://clerk.com/docs/guides/configure/auth-strategies/enterprise-connections/self-serve-sso.md) and you're an Organization [admin](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md)
- [With the Backend API](#with-the-backend-api)

### In the Clerk Dashboard

1. In the Clerk Dashboard, navigate to the [**SSO connections**](https://dashboard.clerk.com/~/user-authentication/sso-connections) page.
2. Select the connection you want to manage the certificates for.
3. Select the **SSO** tab. In the **Identity Provider configuration** section, the **Certificates** list shows every certificate the connection trusts, its expiry date, and which one is the primary. A certificate that expires within 30 days is highlighted, and an expired one is marked in red.
4. To add certificates, select **Add** and choose the file. Clerk accepts `.pem`, `.crt`, `.cer`, and `.cert` files holding a single certificate or a PEM bundle. Clerk adds each certificate as a separate entry and skips any the connection already trusts.
5. To remove a certificate, select the trash icon on its row. You can't remove the last certificate.
6. Select **Save**. Saving other settings won't change the certificate list.

### From `<OrganizationProfile />`

For Organizations with an enterprise connection, the **Security** tab of [<OrganizationProfile />](https://clerk.com/docs/reference/components/organization/organization-profile.md) includes an **Identity provider** section that shows the connection's certificates. Members need the `org:sys_entconns:manage` [System Permission](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md#system-permissions) to manage them.

The default [**Admin**](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md#default-roles) Role includes this Permission. If you've defined custom Roles, add it to any Role whose members should manage the connection's certificates.

Members with this Permission can select **Edit**, then **Configure manually**, to:

- Add certificates to the **Signing certificates** list. To add several at once, upload a PEM bundle.
- Remove certificates from the list.

The same list is available in the [manual configuration step of the self-serve SSO setup](https://clerk.com/docs/guides/configure/auth-strategies/enterprise-connections/self-serve-sso.md#saml-providers).

### With the Backend API

Use the following Backend API endpoints to manage signing certificates from your backend:

- [Create an enterprise connection](https://clerk.com/docs/reference/backend-api/tag/enterprise-connections/POST/enterprise_connections). Set `saml.idp_certificates` to the certificates the new connection should trust.
- [Update an enterprise connection](https://clerk.com/docs/reference/backend-api/tag/enterprise-connections/PATCH/enterprise_connections/%7Benterprise_connection_id%7D). Send the complete `saml.idp_certificates` array, including certificates you want to keep. This replaces the connection's current set.

Each array entry must contain one certificate, in PEM format or as its bare base64 body. Split a PEM bundle into separate entries.

```json
{
  "saml": {
    "idp_certificates": [
      "-----BEGIN CERTIFICATE-----\nMIIC...\n-----END CERTIFICATE-----",
      "-----BEGIN CERTIFICATE-----\nMIID...\n-----END CERTIFICATE-----"
    ]
  }
}
```

An enterprise connection response returns the certificates as objects under `saml_connection.idp_certificates`, with the primary certificate first. Each object contains the certificate as bare base64 and its validity dates as Unix timestamps in milliseconds:

```json
{
  "object": "enterprise_connection",
  "saml_connection": {
    "idp_certificates": [
      {
        "certificate": "MIIC...",
        "issued_at": 1735689600000,
        "expires_at": 1798761600000
      },
      {
        "certificate": "MIID...",
        "issued_at": 1767225600000,
        "expires_at": 1830297600000
      }
    ]
  }
}
```

By contrast, the deprecated [SAML connection endpoints](https://clerk.com/docs/reference/backend-api/tag/saml-connections/PATCH/saml_connections/%7Bsaml_connection_id%7D) return `idp_certificates` at the top level. On both enterprise and SAML connection endpoints, the singular `idp_certificate` input is deprecated in favor of the `idp_certificates` array. The singular input still accepts one certificate or a PEM bundle, but replaces the whole list; sending back only the stored primary certificate discards the others.

To update the connection through the Backend SDK instead, call [`updateEnterpriseConnection()`](https://clerk.com/docs/reference/backend/enterprise-connections/update-enterprise-connection.md) with `saml.idpCertificates`.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
