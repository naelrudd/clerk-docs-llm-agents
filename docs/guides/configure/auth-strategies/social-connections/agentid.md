# Add AgentID as a social connection

**Before you start**

- [A Clerk application is required.](https://clerk.com/docs/getting-started/quickstart/setup-clerk.md)
- [An AgentID account is required.](https://console.agentid.com/sign-up)

Enabling OAuth with [AgentID](https://www.agentid.com/docs) allows your users to sign up and sign in to your Clerk app with their AgentID account.

## Configure for your development instance

For _development instances_, Clerk uses preconfigured shared OAuth credentials and redirect URIs—no other configuration is needed.

1. In the Clerk Dashboard, navigate to the [**SSO connections**](https://dashboard.clerk.com/~/user-authentication/sso-connections) page.
2. Select **Add connection** and select **For all users**.
3. Select **AgentID** from the provider list.

## Configure for your production instance

For _production instances_, you must provide custom credentials.

Keep two browser tabs open during setup: one for the [Clerk Dashboard](https://dashboard.clerk.com/~/user-authentication/sso-connections) and one for your [AgentID console](https://console.agentid.com/).

1. ### Enable AgentID as a social connection in Clerk

   1. In the Clerk Dashboard, navigate to the [**SSO connections**](https://dashboard.clerk.com/~/user-authentication/sso-connections) page.
   2. Select **Add connection** and select **For all users**.
   3. Select **AgentID** from the provider list.
   4. Ensure that both **Enable for sign-up and sign-in** and **Use custom credentials** are toggled on.
   5. Save the **Redirect URI** somewhere secure. Keep this page open.
2. ### Create an AgentID application

   1. In the [AgentID console](https://console.agentid.com/), select **Create application**.
   2. Complete the form as follows:
      - In the **Auth provider** dropdown, select **Clerk**.
      - Under **App name**, enter the name of your app.
      - Under **Redirect URIs**, paste the **Redirect URI** value you saved from the Clerk Dashboard.
      - In the **Token endpoint auth method** dropdown, select `client_secret_basic`.
   3. Select **Create application**. You'll be redirected to your application's page.
   4. Save the **Client ID** and **Client secret** values somewhere secure. The client secret is shown only once. If you lose it, select **Settings** on the application's page and select **Regenerate secret** to issue a new one.
3. ### Set the Client ID and Client Secret in the Clerk Dashboard

   1. Navigate back to the Clerk Dashboard where the configuration page should still be open. Paste the **Client ID** and **Client Secret** values that you saved into the respective fields.
   2. Select **Save**.

   > If the page is no longer open, navigate to the [**SSO connections**](https://dashboard.clerk.com/~/user-authentication/sso-connections) page in the Clerk Dashboard. Select the connection. Under **Use custom credentials**, paste the values into their respective fields.

   > AgentID requires PKCE in addition to client-secret authentication. PKCE binds the authorization code to the sign-in transaction, preventing an intercepted code from being exchanged independently. Clerk enables PKCE automatically for AgentID connections.
4. ### Request the owner's identity

   Clerk requests the `openid`, `email`, and `profile` scopes from AgentID by default. To also receive the identity of the human who owns the agent:

   1. In the Clerk Dashboard, the configuration page should still be open.
   2. Select your **AgentID** connection.
   3. Under **Scopes**, add the `owner_profile` and `owner_email` scopes. The agent's signing credential must permit those claims.
   4. Select **Save**.
5. ### Test your connection

   The simplest way to test your connection is to visit your Clerk app's [Account Portal](https://clerk.com/docs/guides/account-portal/overview.md), which is available for all Clerk apps out-of-the-box.

   1. In the Clerk Dashboard, navigate to the [**Account Portal**](https://dashboard.clerk.com/~/account-portal) page.
   2. Next to **Sign-in**, select the button to visit the sign-in page. The URL should resemble:
      - **For development** - `https://your-domain.accounts.dev/sign-in`
      - **For production** - `https://accounts.your-domain.com/sign-in`
   3. Sign in with your connection's credentials.

   Once you confirm the connection, get the user's OAuth access token from your backend using the [`getUserOauthAccessToken()`](https://clerk.com/docs/reference/backend/user/get-user-oauth-access-token.md) method to retrieve their data from the social provider.

   > Clerk doesn't store the `owner_profile` or `owner_email` claims on the Clerk user. Use the AgentID OAuth access token retrieved above to request them from AgentID's `/userinfo` endpoint.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
