# Platform API errors

An index of Clerk Platform API errors.

## API keys

### <code><wbr />A<wbr />P<wbr />I<wbr />Keys<wbr />Not<wbr />Enabled</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "API Keys not enabled",
      "long_message": "API Keys not enabled",
      "code": "api_keys_not_enabled"
    }
  ]
}
```

## Applications

### <code><wbr />Accountless<wbr />Application<wbr />Managed<wbr />Workspace</code>

`AccountlessApplicationManagedWorkspace` signifies an attempt to claim an accountless
application into a workspace that an integration provider (Vercel Marketplace, Stripe)
manages. Applications in managed workspaces are provisioned by the provider, never claimed.
integrationName must already be the customer-facing name from the managed\_by allowlist;
pass an empty string when the provider is not registered and meta is omitted.

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "Cannot claim into a managed workspace",
      "long_message": "The target application cannot be claimed into the current workspace. Select a different workspace and try again.",
      "code": "accountless_application_managed_workspace",
      "meta": {
        "integration": "<integrationName>"
      }
    }
  ]
}
```

### <code><wbr />Accountless<wbr />Application<wbr />Not<wbr />Found</code>

`AccountlessApplicationNotFound` signifies an error when no application with the given claim token could be found

filename: Status Code: 404
```json
{
  "errors": [
    {
      "message": "Application not found",
      "long_message": "No application was found with the given claim token.",
      "code": "resource_not_found"
    }
  ]
}
```

### <code><wbr />Application<wbr />Already<wbr />Belongs<wbr />To<wbr />Organization</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "already belongs to organization",
      "long_message": "Application already belongs to the selected organization.",
      "code": "application_already_belongs_to_organization"
    }
  ]
}
```

### <code><wbr />Application<wbr />Not<wbr />Found</code>

`ApplicationNotFound` signifies an error when no application with the specified id was found

filename: Status Code: 404
```json
{
  "errors": [
    {
      "message": "Application not found",
      "long_message": "No application was found with the specified id",
      "code": "resource_not_found"
    }
  ]
}
```

### <code><wbr />Application<wbr />Transfer<wbr />Already<wbr />In<wbr />Progress</code>

`ApplicationTransferAlreadyInProgress` signifies that an application transfer has already
been attempted, but did not complete successfully.

filename: Status Code: 409
```json
{
  "errors": [
    {
      "message": "transfer already in progress",
      "long_message": "An application transfer is already in progress. Please contact support for assistance.",
      "code": "application_transfer_already_in_progress"
    }
  ]
}
```

### <code><wbr />Application<wbr />Transfer<wbr />Not<wbr />Pending</code>

`ApplicationTransferNotPending` signifies that the application transfer is not in pending status
and cannot be canceled.

filename: Status Code: 409
```json
{
  "errors": [
    {
      "message": "transfer not pending",
      "long_message": "The application transfer is not in pending status and cannot be canceled.",
      "code": "application_transfer_not_pending"
    }
  ]
}
```

### <code><wbr />Cannot<wbr />Transfer<wbr />App<wbr />With<wbr />Unsupported<wbr />Features</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "cannot transfer application with unsupported features",
      "long_message": "The application uses features that are not supported by the target workspace's plan. Upgrade the target workspace or remove the unsupported features from the application.",
      "code": "transfer_app_with_unsupported_features",
      "meta": {
        "unsupported_features": [
          "<unsupportedFeatures>"
        ]
      }
    }
  ]
}
```

### <code><wbr />Cannot<wbr />Transfer<wbr />Old<wbr />Paid<wbr />App<wbr />To<wbr />New<wbr />Pricing<wbr />Workspace</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "cannot transfer paid application to workspace with new pricing",
      "long_message": "Paid applications can't be moved into workspaces with the new pricing. Choose a workspace on the legacy pricing instead.",
      "code": "transfer_old_paid_app_to_new_pricing_workspace"
    }
  ]
}
```

### <code><wbr />Cannot<wbr />Transfer<wbr />Paid<wbr />App<wbr />To<wbr />Account<wbr />Without<wbr />Billing<wbr />Information</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "cannot transfer paid application, missing billing info",
      "long_message": "Paid applications can only be transferred to personal workspaces or organizations with billing info. Add the necessary billing info and try again.",
      "code": "transfer_paid_app_to_free_account"
    }
  ]
}
```

### <code><wbr />Cannot<wbr />Transfer<wbr />To<wbr />Account<wbr />Without<wbr />Payment<wbr />Method</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "cannot transfer paid application, missing payment method",
      "long_message": "The selected account doesn't have any payment methods associated with it.",
      "code": "transfer_paid_app_to_account_no_payment_method"
    }
  ]
}
```

### <code><wbr />Invalid<wbr />Application<wbr />Name</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "invalid application name",
      "long_message": "The application name \"<name>\" is invalid: <reason>",
      "code": "form_param_value_invalid",
      "meta": {
        "param_name": "name"
      }
    }
  ]
}
```

### <code><wbr />Not<wbr />Authorized<wbr />To<wbr />Delete<wbr />System<wbr />Application</code>

`NotAuthorizedToDeleteSystemApplication` signifies an error when trying to delete a system application

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "Unauthorized request",
      "long_message": "You are not authorized to delete system application <applicationID>",
      "code": "authorization_invalid"
    }
  ]
}
```

### <code><wbr />Workspace<wbr />Not<wbr />Configured</code>

`WorkspaceNotConfigured` is returned when the workspace is missing
configuration required to complete the operation (for example, a role
or feature that has not yet been provisioned).

filename: Status Code:&#x20;
```json
{
  "errors": [
    {
      "message": "workspace not configured",
      "long_message": "Workspace is not configured for this operation.",
      "code": "workspace_not_configured"
    }
  ]
}
```

## Auth

### <code><wbr />Authorization<wbr />Missing<wbr />Scopes</code>

`AuthorizationMissingScopes` signifies that the authorization is missing required scope(s).
Returns a 403 Forbidden error.

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "Missing authorization scopes",
      "long_message": "Missing authorization scopes",
      "code": "authorization_missing_scopes",
      "meta": {
        "scopes": [
          "<missing>"
        ]
      }
    }
  ]
}
```

### <code><wbr />Could<wbr />Not<wbr />Authenticate<wbr />Request</code>

filename: Status Code: 401
```json
{
  "errors": [
    {
      "message": "Could not authenticate request.",
      "long_message": "Could not authenticate request.",
      "code": "could_not_authenticate_request"
    }
  ]
}
```

### <code><wbr />Identification<wbr />Exists</code>

`IdentificationExists` signifies an error when the identifier already exists

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "already exists",
      "long_message": "This <identifier> already exists.",
      "code": ""
    }
  ]
}
```

### <code><wbr />Identifier<wbr />Not<wbr />Allowed<wbr />Access</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "Access not allowed.",
      "long_message": "<who> <pluralization> not allowed to access this application.",
      "code": "not_allowed_access",
      "meta": {
        "identifiers": [
          "<identifiers>"
        ]
      }
    }
  ]
}
```

### <code><wbr />Invalid<wbr />Authorization</code>

`InvalidAuthorization` signifies an error when the request is not authorized to perform the given operation

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "Unauthorized request",
      "long_message": "You are not authorized to perform this request",
      "code": "authorization_invalid"
    }
  ]
}
```

### <code><wbr />Invalid<wbr />Authorization<wbr />Header<wbr />Format</code>

`InvalidAuthorizationHeaderFormat` signifies an error when the Authorization header has no proper format.

filename: Status Code: 401
```json
{
  "errors": [
    {
      "message": "Invalid Authorization header format",
      "long_message": "Invalid Authorization header format. Must be 'Bearer <YOUR_API_KEY>'",
      "code": "authorization_header_format_invalid"
    }
  ]
}
```

### <code><wbr />Invalid<wbr />User<wbr />Settings</code>

`InvalidUserSettings` signifies an error where the auth settings of the instance
are not well configured, which results in sign in and sign up endpoints to be
restricted.

filename: Status Code: 409
```json
{
  "errors": [
    {
      "message": "invalid auth configuration",
      "long_message": "The authentication settings are invalid.",
      "code": "user_settings_invalid"
    }
  ]
}
```

### <code><wbr />Subaddress<wbr />Restriction<wbr />Email<wbr />Already<wbr />Used</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "This email address is already in use.",
      "long_message": "This email address is already in use. Creating multiple accounts with the same email address is not allowed.",
      "code": "not_allowed_access"
    }
  ]
}
```

### <code><wbr />Unsupported<wbr />Country</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "Unsupported country code",
      "long_message": "Phone numbers from this country (<countryName>) are currently not supported. For more information, please contact <support>.",
      "code": "unsupported_country_code",
      "meta": {
        "alpha2": "<alpha2>",
        "country_code": "<countryCode>"
      }
    }
  ]
}
```

## Commerce

### <code><wbr />Billing<wbr />Annual<wbr />Only<wbr />Plans<wbr />Not<wbr />Enabled</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "Annual only plans are not enabled",
      "long_message": "Annual only plans are not enabled, please enable the update in Clerk dashboard.",
      "code": "billing_annual_only_plans_not_enabled"
    }
  ]
}
```

### <code><wbr />Billing<wbr />Cannot<wbr />Be<wbr />Disabled</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Cannot disable Billing",
      "long_message": "Cannot disable Billing because <reason>.",
      "code": "billing_cannot_be_disabled"
    }
  ]
}
```

### <code><wbr />Billing<wbr />Cannot<wbr />Be<wbr />Enabled</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Cannot enable Billing",
      "long_message": "Cannot enable Billing because <reason>.",
      "code": "billing_cannot_be_enabled"
    }
  ]
}
```

### <code><wbr />Billing<wbr />Too<wbr />Few<wbr />Free<wbr />Trial<wbr />Days</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Invalid free trial days",
      "long_message": "Free trial days must be at least 1 day",
      "code": "billing_too_few_free_trial_days"
    }
  ]
}
```

### <code><wbr />Billing<wbr />Too<wbr />Many<wbr />Free<wbr />Trial<wbr />Days</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Invalid free trial days",
      "long_message": "Free trial days must be at most 365 days",
      "code": "billing_too_many_free_trial_days"
    }
  ]
}
```

### <code><wbr />Commerce<wbr />Insufficient<wbr />Seats</code>

filename: Status Code: 402
```json
{
  "errors": [
    {
      "message": "Insufficient seats",
      "long_message": "You have reached the seat limit for your current plan.",
      "code": "insufficient_seats",
      "meta": {
        "seats_quantity_to_add": 0,
        "seats_quantity": 0
      }
    }
  ]
}
```

### <code><wbr />Currency<wbr />Invalid</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Invalid currency",
      "long_message": "Currency is not supported",
      "code": "currency_invalid"
    }
  ]
}
```

### <code><wbr />Default<wbr />Plan<wbr />Amount<wbr />Update<wbr />Forbidden</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Default plan amount update forbidden",
      "long_message": "Default plan pricing cannot be modified. Only paid plans support amount updates",
      "code": "default_plan_amount_update_forbidden"
    }
  ]
}
```

### <code><wbr />Free<wbr />Trial<wbr />Not<wbr />Allowed<wbr />On<wbr />Free<wbr />Plan</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Free trial not allowed on free plan",
      "long_message": "Free trials cannot be enabled on free plans",
      "code": "free_trial_not_allowed_on_free_plan"
    }
  ]
}
```

### <code><wbr />Missing<wbr />Name</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Missing name",
      "long_message": "Name is required to perform this operation",
      "code": "missing_name"
    }
  ]
}
```

### <code><wbr />Missing<wbr />Slug</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Missing slug",
      "long_message": "Slug is required to perform this operation",
      "code": "missing_slug"
    }
  ]
}
```

### <code><wbr />Name<wbr />Invalid<wbr />Format</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Invalid  name format",
      "long_message": "Name cannot contain colons (:)",
      "code": "name_invalid_format",
      "meta": {
        "param_name": "name"
      }
    }
  ]
}
```

### <code><wbr />Name<wbr />Invalid<wbr />Length</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Name length is invalid",
      "long_message": "Name must be between <minLen> and <maxLen> characters",
      "code": "name_invalid_length",
      "meta": {
        "param_name": "name"
      }
    }
  ]
}
```

### <code><wbr />Payer<wbr />Type<wbr />Invalid</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Invalid payer type",
      "long_message": "Payer type is invalid",
      "code": "payer_type_invalid"
    }
  ]
}
```

### <code><wbr />Plan<wbr />Amount<wbr />Invalid</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Paid plan month or annual fee invalid",
      "long_message": "Paid plan month or annual fee invalid",
      "code": "plan_amount_invalid"
    }
  ]
}
```

### <code><wbr />Plan<wbr />Amount<wbr />Too<wbr />Large</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Paid plan monthly base fee exceeds upper limit",
      "long_message": "Paid plan monthly base fee must be less than $999,999.99",
      "code": "plan_amount_exceeds_upper_limit"
    }
  ]
}
```

### <code><wbr />Plan<wbr />Cannot<wbr />Be<wbr />Deleted</code>

filename: Status Code: 409
```json
{
  "errors": [
    {
      "message": "Plan cannot be deleted",
      "long_message": "This plan cannot be deleted because <reason>.",
      "code": "plan_cannot_be_deleted"
    }
  ]
}
```

### <code><wbr />Plan<wbr />Name<wbr />Already<wbr />Exists</code>

filename: Status Code: 409
```json
{
  "errors": [
    {
      "message": "Plan name already exists",
      "long_message": "Plan name already exists",
      "code": "plan_name_already_exists",
      "meta": {
        "param_name": "name"
      }
    }
  ]
}
```

### <code><wbr />Product<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "errors": [
    {
      "message": "Product not found",
      "long_message": "Product not found",
      "code": "product_not_found"
    }
  ]
}
```

### <code><wbr />Slug<wbr />Invalid<wbr />Format</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Invalid slug format",
      "long_message": "Slug must only use letters, numbers, dashes (-), and underscores (_). Colons and other characters are not allowed.",
      "code": "slug_invalid_format",
      "meta": {
        "param_name": "slug"
      }
    }
  ]
}
```

### <code><wbr />Slug<wbr />Invalid<wbr />Length</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Slug length is invalid",
      "long_message": "Slug must be between <minLen> and <maxLen> characters",
      "code": "slug_invalid_length",
      "meta": {
        "param_name": "slug"
      }
    }
  ]
}
```

### <code><wbr />Supported<wbr />Billing<wbr />Period<wbr />Mismatch</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Supported billing period mismatch",
      "long_message": "<field> cannot be set when supported_billing_periods is \"<period>\"",
      "code": "supported_billing_period_mismatch",
      "meta": {
        "param_name": "<field>"
      }
    }
  ]
}
```

## Config

### <code><wbr />Config<wbr />Validation<wbr />Error</code>

`ConfigValidationError` returns a 422 error with schema path

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "",
      "long_message": "",
      "code": "config_validation_error",
      "meta": {
        "config_key": "<configKey>",
        "param_name": "<paramName>",
        "schema_path": "<schemaPath>"
      }
    }
  ]
}
```

### <code><wbr />Config<wbr />Version<wbr />Conflict</code>

`ConfigVersionConflict` returns a 409 error for ETag mismatch

filename: Status Code: 409
```json
{
  "errors": [
    {
      "message": "Config version conflict",
      "long_message": "Config was modified since last read. Re-fetch and retry.",
      "code": "config_version_conflict",
      "meta": {
        "current_version": "<currentVersion>",
        "provided_version": "<providedVersion>"
      }
    }
  ]
}
```

### <code><wbr />Destructive<wbr />Operation<wbr />Not<wbr />Allowed</code>

`DestructiveOperationNotAllowed` returns a 400 error

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Cannot clear config key '<key>' without destructive=true",
      "long_message": "Cannot clear config key '<key>' without destructive=true",
      "code": "destructive_operation_not_allowed",
      "meta": {
        "param_name": "<key>"
      }
    }
  ]
}
```

### <code><wbr />Invalid<wbr />Config<wbr />Key<wbr />Body</code>

`InvalidConfigKeyBody` returns a 400 error indicating the value for a config
key has the wrong shape (e.g. an array of objects where the schema expects
an array of strings).

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Request body invalid for config key '<key>'",
      "long_message": "The value for config key '<key>' does not match the expected schema.",
      "code": "config_key_body_invalid",
      "meta": {
        "param_name": "<key>"
      }
    }
  ]
}
```

### <code><wbr />Missing<wbr />Config<wbr />Keys</code>

`MissingConfigKeys` returns a 400 error listing keys that were not included in a PUT request

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Missing config keys",
      "long_message": "PUT requires all config keys to be included. Some keys are missing.",
      "code": "missing_config_keys",
      "meta": {
        "missing_keys": [
          "<missing>"
        ]
      }
    }
  ]
}
```

### <code><wbr />Unknown<wbr />Config<wbr />Key</code>

`UnknownConfigKey` returns a 400 error with typo suggestions

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Unknown config key '<key>'",
      "long_message": "Unknown config key '<key>'",
      "code": "unknown_config_key"
    }
  ]
}
```

## Domains

### <code><wbr />Domain<wbr />Create<wbr />Intent<wbr />Name<wbr />Mismatch</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Domain create was invalid",
      "long_message": "Domain name must match the name associated with the domain intent",
      "code": "domain_create_intent_name_mismatch"
    }
  ]
}
```

### <code><wbr />Operation<wbr />Not<wbr />Allowed<wbr />On<wbr />Primary<wbr />Domain</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "operation not allowed",
      "long_message": "This operation is not allowed on a primary domain. Try again with a satellite domain of the instance.",
      "code": "operation_not_allowed_on_primary_domain"
    }
  ]
}
```

### <code><wbr />Proxy<wbr />U<wbr />R<wbr />L<wbr />Required<wbr />For<wbr />Provider<wbr />Domain</code>

`ProxyURLRequiredForProviderDomain` signifies an error when a provider domain
(e.g., replit.app, vercel.app) is created without a proxy URL.

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "proxy URL required",
      "long_message": "Provider domain <domainName> requires a proxy URL. Provider domains must be configured with a proxy.",
      "code": "proxy_url_required_for_provider_domain",
      "meta": {
        "param_name": "<paramName>"
      }
    }
  ]
}
```

## Features

### <code><wbr />Feature<wbr />In<wbr />Use</code>

filename: Status Code: 409
```json
{
  "errors": [
    {
      "message": "Feature in use",
      "long_message": "Feature is in use",
      "code": "feature_in_use"
    }
  ]
}
```

### <code><wbr />Feature<wbr />Not<wbr />Enabled</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "not enabled",
      "long_message": "This feature is not enabled on this instance",
      "code": "feature_not_enabled"
    }
  ]
}
```

### <code><wbr />Feature<wbr />Not<wbr />Enabled<wbr />With<wbr />Meta</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "not enabled",
      "long_message": "This feature is not enabled on this instance",
      "code": "feature_not_enabled",
      "meta": {
        "param_name": "<paramName>"
      }
    }
  ]
}
```

### <code><wbr />Feature<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "errors": [
    {
      "message": "Feature not found",
      "long_message": "Feature not found",
      "code": "feature_not_found"
    }
  ]
}
```

### <code><wbr />Not<wbr />Implemented</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "not implemented",
      "long_message": "Feature `<feature>` is not available yet",
      "code": "feature_not_implemented"
    }
  ]
}
```

## Forms

### <code><wbr />Form<wbr />Already<wbr />Exists</code>

`FormAlreadyExists` signifies an error when given resource already exists

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "The <parameter> already exists. Please try another.",
      "long_message": "The <parameter> already exists. Please try another.",
      "code": "form_already_exists",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Already<wbr />Exists<wbr />By<wbr />Provider<wbr />Managed<wbr />Domain</code>

`FormAlreadyExistsByProviderManagedDomain` signifies an error when a domain
already exists on an app managed by an external provider.

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Domain already in use by a <providerName> app",
      "long_message": "The <domain> root domain is already in use by a <providerName> app. Delete the <providerName> app or contact <providerName> support to remove the domain before using it in Clerk.",
      "code": "form_already_exists",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Disallow<wbr />Future<wbr />Date</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Date values must not be in the future.",
      "long_message": "Date values must not be in the future.",
      "code": "form_disallow_future_date",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Duplicate<wbr />Parameter</code>

`FormDuplicateParameter` signifies an error when a duplicate parameter is found in a form

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is duplicate",
      "long_message": "<param> included multiple times. There should only be one.",
      "code": "form_param_duplicate",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Identifier<wbr />Exists</code>

`FormIdentifierExists` signifies an error when given identifier already exists

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "That <parameter> is taken. Please try another.",
      "long_message": "That <parameter> is taken. Please try another.",
      "code": "form_identifier_exists",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Identifier<wbr />Exists<wbr />With<wbr />Another<wbr />Account</code>

`FormIdentifierExistsWithAnotherAccount` signifies an error when given identifier already exists.
This is used to signal to a user that the identifier, phone number, is already associated with another account and should remove it from the other account.

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "This <parameter> is already associated with an existing account. To use this <parameter> with this account, please remove it from your existing account first.",
      "long_message": "This <parameter> is already associated with an existing account. To use this <parameter> with this account, please remove it from your existing account first.",
      "code": "form_identifier_exists",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Date</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Date values must be given in Unix millisecond timestamp format.",
      "long_message": "Date values must be given in Unix millisecond timestamp format.",
      "code": "form_param_invalid_date",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Email<wbr />Address</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is invalid",
      "long_message": "<parameter> must be a valid email address.",
      "code": "form_param_format_invalid",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Encoding<wbr />Parameter<wbr />Value</code>

`FormInvalidEncodingParameterValue` signifies an error when the given parameter has an invalid encoding

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "invalid character encoding",
      "long_message": "<param> contains invalid UTF-8 characters",
      "code": "form_param_value_invalid",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Inactivity<wbr />Timeout<wbr />Against<wbr />Time<wbr />To<wbr />Expire</code>

`FormInvalidInactivityTimeoutAgainstTimeToExpire` signifies an error when the session inactivity timeout is greater than session time to expire

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is invalid",
      "long_message": "Session inactivity timeout must be lower than maximum session lifetime.",
      "code": "form_session_inactivity_timeout_invalid",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Parameter<wbr />Format</code>

`FormInvalidParameterFormat` signifies an error when the given parameter has an invalid format

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "<parameter> is invalid.<details>",
      "long_message": "<parameter> is invalid.<details>",
      "code": "form_param_format_invalid",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Parameter<wbr />Format<wbr />B<wbr />C<wbr />P47</code>

`FormInvalidParameterFormatBCP47` signifies an error when the given parameter does not match the BCP-47 format

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is invalid",
      "long_message": "<parameter> must be a valid BCP-47 language tag.",
      "code": "form_param_format_invalid",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Parameter<wbr />Value</code>

`FormInvalidParameterValue` signifies an error when the given parameter has an invalid value

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is invalid",
      "long_message": "<value> does not match one of the allowed values for parameter <param>",
      "code": "form_param_value_invalid",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Parameter<wbr />Value<wbr />Must<wbr />Be<wbr />Not<wbr />Empty</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is invalid",
      "long_message": "<param> is invalid. Must be not empty",
      "code": "form_param_value_invalid",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Parameter<wbr />Value<wbr />With<wbr />Allowed</code>

`FormInvalidParameterValueWithAllowed` signifies an error when the given parameter has an invalid value.
The difference with FormInvalidParameterValue is that this error also includes the allowed values

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is invalid",
      "long_message": "<value> does not match the allowed values for parameter <param>. Allowed values: <allowedValues>",
      "code": "form_param_value_invalid",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />Length<wbr />Too<wbr />Long</code>

`FormInvalidPasswordLengthTooLong` signifies an error when the password is invalid because of its length

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Passwords must be less than <maxLen> characters.",
      "long_message": "Passwords must be less than <maxLen> characters.",
      "code": "form_password_length_too_long",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />Length<wbr />Too<wbr />Short</code>

`FormInvalidPasswordLengthTooShort` signifies an error when the password is invalid because of its length

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Passwords must be <minLen> characters or more.",
      "long_message": "Passwords must be <minLen> characters or more.",
      "code": "form_password_length_too_short",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />No<wbr />Lowercase</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Passwords must contain at least one lowercase character.",
      "long_message": "Passwords must contain at least one lowercase character.",
      "code": "form_password_no_lowercase",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />No<wbr />Number</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Passwords must contain at least one number.",
      "long_message": "Passwords must contain at least one number.",
      "code": "form_password_no_number",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />No<wbr />Special<wbr />Char</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Passwords must contain at least one of the following special characters: <allowedSpecialChars>.",
      "long_message": "Passwords must contain at least one of the following special characters: <allowedSpecialChars>.",
      "code": "form_password_no_special_char",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />Not<wbr />Strong<wbr />Enough</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Given password is not strong enough.",
      "long_message": "Given password is not strong enough.",
      "code": "form_password_not_strong_enough",
      "meta": {
        "param_name": "<param>",
        "zxcvbn": {
          "suggestions": [
            "<suggestions>"
          ]
        }
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />No<wbr />Uppercase</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Passwords must contain at least one uppercase character.",
      "long_message": "Passwords must contain at least one uppercase character.",
      "code": "form_password_no_uppercase",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />Size<wbr />In<wbr />Bytes<wbr />Exceeded</code>

`FormInvalidPasswordSizeInBytesExceeded` signifies that the size in bytes was exceeded.
Note that the maximum character length constraint may fail to detect this case,
if multi-byte characters are included in the password.
For example, bcrypt limit https://cs.opensource.google/go/x/crypto/+/refs/tags/v0.8.0:bcrypt/bcrypt.go;l=87

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Your password is too long. Please use a shorter one.",
      "long_message": "Your password is too long. Please use a shorter one.",
      "code": "form_password_size_in_bytes_exceeded",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Phone<wbr />Number</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is invalid",
      "long_message": "<parameter> must be a valid phone number according to E.164 international standard.",
      "code": "form_param_format_invalid",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Time</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "invalid format",
      "long_message": "<param> must contain a datetime specified in RFC3339 format (e.g. `2022-10-20T10:00:27.645Z`).",
      "code": "form_param_invalid_time",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Type<wbr />Parameter</code>

`FormInvalidTypeParameter` signifies an error when a form parameter has the wrong type

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is invalid",
      "long_message": "`<param>` must be a `<paramType>`.",
      "code": "form_param_type_invalid",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Username<wbr />Character</code>

`FormInvalidUsernameCharacter` signifies an error when the given username does not match username regex

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "<parameter> can only contain <allowedCharsString>.",
      "long_message": "<parameter> can only contain <allowedCharsString>.",
      "code": "form_username_invalid_character",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Username<wbr />Length</code>

`FormInvalidUsernameLength` signifies an error when the given username does not have required length

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "<parameter> must be between <mininum> and <maximum> characters long.",
      "long_message": "<parameter> must be between <mininum> and <maximum> characters long.",
      "code": "form_username_invalid_length",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Username<wbr />Needs<wbr />Non<wbr />Number<wbr />Char<wbr />Code</code>

`FormInvalidUsernameNeedsNonNumberCharCode` signifies an error when the given username does not match username regex

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "<parameter> must contain one non-number character.",
      "long_message": "<parameter> must contain one non-number character.",
      "code": "form_username_needs_non_number_char",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Web3<wbr />Wallet<wbr />Address</code>

`FormInvalidWeb3WalletAddress` signifies an error when the given web3 wallet address is invalid

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is invalid",
      "long_message": "<parameter> must be a valid web3 wallet address.",
      "code": "form_param_format_invalid",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Metadata<wbr />Invalid<wbr />Type</code>

`FormMetadataInvalidType` signifies an error when the given metadata is not a valid key-value object

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "<key> must be a valid key-value object. To reset the <metadataType>, use an empty object (\"{}\").",
      "long_message": "<key> must be a valid key-value object. To reset the <metadataType>, use an empty object (\"{}\").",
      "code": "form_param_value_invalid",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Missing<wbr />Conditional<wbr />Parameter</code>

`FormMissingConditionalParameter` signifies an error when required parameter based on conditions is missing

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is missing",
      "long_message": "`<param>` is required when `<leftCondition>` is `<rightCondition>`.",
      "code": "form_conditional_param_missing",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Missing<wbr />Conditional<wbr />Parameter<wbr />On<wbr />Existence</code>

`FormMissingConditionalParameterOnExistence` signifies an error when parameter is required because of the existence of another

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is missing",
      "long_message": "`<missingParam>` is required when `<conditionalParam>` is present.",
      "code": "form_conditional_param_missing",
      "meta": {
        "param_name": "<missingParam>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Missing<wbr />Parameter</code>

`FormMissingParameter` signifies an error when an expected form parameter is missing

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is missing",
      "long_message": "<param> must be included.",
      "code": "form_param_missing",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Nil<wbr />Parameter</code>

`FormNilParameter` signifies an error when a nil parameter is found in a form

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Enter <parameter>.",
      "long_message": "Enter <parameter>.",
      "code": "form_param_nil",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Array<wbr />Length<wbr />Mismatch</code>

`FormParameterArrayLengthMismatch` signifies an error when a parallel array
parameter does not have the same number of items as the array it qualifies.

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "length mismatch",
      "long_message": "<parameter> must contain exactly one item for each item in <otherParam>.",
      "code": "form_param_array_length_mismatch",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Array<wbr />Size<wbr />Exceeded</code>

`FormParameterArraySizeExceeded` signifies an error when the given array exceeds the maximum allowed size

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "exceeds maximum size",
      "long_message": "<parameter> should not exceed <maximum> items.",
      "code": "form_param_array_size_exceeded",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Max<wbr />Length<wbr />Exceeded</code>

`FormParameterMaxLengthExceeded` signifies an error when the given param value exceeds the maximum allowed length

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "exceeds maximum length",
      "long_message": "<parameter> should not exceed <maximum> characters.",
      "code": "form_param_max_length_exceeded",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Not<wbr />Allowed<wbr />Conditionally</code>

`FormParameterNotAllowedConditionally` signifies an error when parameter is not allowed based on condition

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is not allowed",
      "long_message": "`<param>` isn't allowed when `<leftCondition>` is <rightCondition>.",
      "code": "form_conditional_param_disallowed",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Not<wbr />Allowed<wbr />If<wbr />Another<wbr />Parameter<wbr />Is<wbr />Present</code>

`FormParameterNotAllowedIfAnotherParameterIsPresent` signifies an error when a parameter is present but
is not allowed because another parameter is also present

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is not allowed",
      "long_message": "`<notAllowedParam>` isn't allowed when `<existingParam>` is present.",
      "code": "form_conditional_param_disallowed",
      "meta": {
        "param_name": "<notAllowedParam>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Size<wbr />Too<wbr />Large</code>

`FormParameterSizeTooLarge` signifies an error when a parameter exceeds the max allowed size

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "The given <param> exceeds the maximum allowed size of <maxByteSize> bytes (<maxSizeInKb> KB).",
      "long_message": "The given <param> exceeds the maximum allowed size of <maxByteSize> bytes (<maxSizeInKb> KB).",
      "code": "form_param_exceeds_allowed_size",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Value<wbr />Not<wbr />Allowed<wbr />Conditionally</code>

`FormParameterValueNotAllowedConditionally` signifies an error when parameter value is not allowed based on condition

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "<value> is not allowed",
      "long_message": "`<value>` isn't allowed for `<param>` when <leftCondition> is <rightCondition>.",
      "code": "form_conditional_param_value_disallowed",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Value<wbr />Too<wbr />Large</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Value too large",
      "long_message": "The value of <param> can't be greater than <maximum>",
      "code": "form_param_value_too_large",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Password<wbr />Digest<wbr />Invalid</code>

`FormPasswordDigestInvalid` signifies an error when the provided password\_digest is not valid for the provided password\_hasher

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "The provided <param> is not a valid <hasher> password hash.",
      "long_message": "The provided <param> is not a valid <hasher> password hash.",
      "code": "form_password_digest_invalid_code",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Password<wbr />Matches<wbr />Identifier</code>

`FormPasswordMatchesIdentifier` signifies an error when the chosen password
is identical to one of the account's identifiers (email address, phone
number or username).

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Password cannot match your email address, phone number or username. For account safety, please use a different password.",
      "long_message": "Password cannot match your email address, phone number or username. For account safety, please use a different password.",
      "code": "form_password_matches_identifier",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Password<wbr />Validation<wbr />Failed</code>

`FormPasswordValidationFailed` signifies a generic error when the password validation failed

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Incorrect password. Please try again.",
      "long_message": "Incorrect password. Please try again.",
      "code": "form_password_validation_failed",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Public<wbr />Client<wbr />Requires<wbr />P<wbr />K<wbr />C<wbr />E</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is invalid",
      "long_message": "PKCE is required for OAuth clients without a secret",
      "code": "form_public_client_requires_pkce",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Pwned<wbr />Password</code>

`FormPwnedPassword` signifies an error when the chosen password has been found in the pwned list

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Password has been found in an online data breach. For account safety, please <action>.",
      "long_message": "Password has been found in an online data breach. For account safety, please <action>.",
      "code": "form_password_pwned",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Unknown<wbr />Parameter<wbr />Due<wbr />To<wbr />Disabled<wbr />Feature</code>

`FormUnknownParameterDueToDisabledFeature` signifies an error when an unexpected parameter is found in a form due to a disabled feature

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is unknown",
      "long_message": "<param> is not a valid parameter for this request.<possibleResolution>",
      "code": "form_param_unknown",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Username<wbr />Cannot<wbr />Be<wbr />Phone<wbr />Number</code>

`FormUsernameCannotBePhoneNumber` signifies an error when the given username
is in canonical E.164 phone-number format. This is rejected regardless of
the configured username character set so that the value remains reserved
for the phone-number identifier and avoids ambiguity at sign-in.

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "<parameter> cannot be a phone number.",
      "long_message": "<parameter> cannot be a phone number. Please choose a different username.",
      "code": "form_username_cannot_be_phone_number",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Form<wbr />Validation<wbr />Failed</code>

`FormValidationFailed` converts validator.ValidationErrors to Error.

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is invalid",
      "long_message": "<sanitizedField> is invalid",
      "code": "form_param_value_invalid",
      "meta": {
        "param_name": "<sanitizedField>"
      }
    }
  ]
}
```

## Home URL

### <code><wbr />Home<wbr />U<wbr />R<wbr />L<wbr />Taken</code>

`HomeURLTaken` signifies an error when the root domain of the provided home\_url already in use by another application

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Domain already in use",
      "long_message": "The <homeURL> root domain is already in use by another application.",
      "code": "home_url_taken",
      "meta": {
        "param_name": "<paramName>"
      }
    }
  ]
}
```

### <code><wbr />Known<wbr />Hosting<wbr />Domain</code>

`KnownHostingDomain` signifies an error when the domain extracted from the provided home\_url belongs to a
known hosting service and cannot be used to deploy production apps

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Known hosting domain",
      "long_message": "The <domain> domain cannot be used to deploy production apps.",
      "code": "known_hosting_domain",
      "meta": {
        "param_name": "<paramName>"
      }
    }
  ]
}
```

### <code><wbr />Reserved<wbr />Domain</code>

`ReservedDomain` signifies an error when the domain extracted from the provided home\_url is reserved by Clerk

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Domain reserved by Clerk",
      "long_message": "The <domain> domain is reserved by Clerk.",
      "code": "reserved_domain",
      "meta": {
        "param_name": "<paramName>"
      }
    }
  ]
}
```

### <code><wbr />Reserved<wbr />Subdomain</code>

`ReservedSubdomain` signifies an error when the subdomain extracted from the provided home\_url is reserved by Clerk

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Reserved subdomain",
      "long_message": "The <subdomain> subdomain is reserved by Clerk.",
      "code": "reserved_subdomain",
      "meta": {
        "param_name": "<paramName>"
      }
    }
  ]
}
```

## Images

### <code><wbr />Image<wbr />Decoding<wbr />Failed</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Image decode error",
      "long_message": "The image could not be decoded. Please ensure the image is valid and try again.",
      "code": "request_body_invalid"
    }
  ]
}
```

### <code><wbr />Image<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "errors": [
    {
      "message": "Image not found",
      "long_message": "Image not found",
      "code": "image_not_found"
    }
  ]
}
```

### <code><wbr />Image<wbr />Too<wbr />Large</code>

`ImageTooLarge` signifies an error when the image being uploaded is too large to handle.

filename: Status Code: 413
```json
{
  "errors": [
    {
      "message": "Image too large",
      "long_message": "The image being uploaded is more than 10MB. Please choose a smaller one.",
      "code": "image_too_large"
    }
  ]
}
```

### <code><wbr />Image<wbr />Type<wbr />Not<wbr />Supported</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Unsupported image type",
      "long_message": "'<imageType>' images are not currently supported. Please consult the API documentation for more information.",
      "code": "request_body_invalid"
    }
  ]
}
```

### <code><wbr />Request<wbr />Without<wbr />Image</code>

`RequestWithoutImage` signifies an error when no image was present in the request.

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Image file missing",
      "long_message": "There was no image file present in the request",
      "code": "form_param_missing"
    }
  ]
}
```

## Instance settings

### <code><wbr />Invalid<wbr />Captcha<wbr />Widget<wbr />Type</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Invalid captcha widget type",
      "long_message": "The captcha widget type '<widgetType>' is invalid. Allowed values: <allowedTypes>",
      "code": "invalid_captcha_widget_type"
    }
  ]
}
```

### <code><wbr />Invalid<wbr />Captcha<wbr />Widget<wbr />Type<wbr />Transition</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Invalid captcha widget type transition",
      "long_message": "The captcha widget type cannot be changed from '<from>' to '<to>'.",
      "code": "invalid_captcha_widget_type"
    }
  ]
}
```

## Instances

### <code><wbr />Instance<wbr />Not<wbr />Found</code>

`InstanceNotFound` signifies an error when no instance with given instanceID was found

filename: Status Code: 404
```json
{
  "errors": [
    {
      "message": "Instance not found",
      "long_message": "No instance was found with id <instanceID>",
      "code": "resource_not_found"
    }
  ]
}
```

### <code><wbr />Production<wbr />Instance<wbr />Exists</code>

`ProductionInstanceExists` signifies an error when trying to create a production instance
when there is already one

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "You can only have one production instance.",
      "long_message": "You can only have one production instance.",
      "code": "production_instance_exists"
    }
  ]
}
```

## Internal

### <code><wbr />Bad<wbr />Request<wbr />With<wbr />Message</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "",
      "long_message": "",
      "code": "bad_request"
    }
  ]
}
```

### <code><wbr />Conflict</code>

409 - conflict.
This apierror provides very little context and should likely be avoided for
errors that will be customer- or end-user-facing. For lock errors, consider
instead ResourceBusy().

filename: Status Code: 409
```json
{
  "errors": [
    {
      "message": "Conflict",
      "long_message": "Conflict",
      "code": "conflict"
    }
  ]
}
```

### <code><wbr />Quota<wbr />Exceeded</code>

403 - quota exceeded

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "Quota exceeded",
      "long_message": "Quota exceeded, you have reached your limit.",
      "code": "quota_exceeded"
    }
  ]
}
```

### <code><wbr />Resource<wbr />Busy</code>

409 - resource locked

filename: Status Code: 409
```json
{
  "errors": [
    {
      "message": "resource busy",
      "long_message": "This resource is currently being modified by another request. Please try again.",
      "code": "resource_locked"
    }
  ]
}
```

### <code><wbr />Service<wbr />Unavailable</code>

503 - service unavailable
Unwraps the error chain to check if an API error was wrapped,
and returns that instead of creating a 503 error

filename: Status Code: 503
```json
{
  "errors": [
    {
      "message": "Service unavailable",
      "long_message": "Service unavailable",
      "code": "service_unavailable"
    }
  ]
}
```

### <code><wbr />Unexpected</code>

`Unexpected` is used for all unexpected errors
It unwraps the error chain to check if an API error was wrapped,
and returns that instead of creating a 500 error

filename: Status Code: 500
```json
{
  "errors": [
    {
      "message": "Oops, an unexpected error occurred",
      "long_message": "There was an internal error on our servers. We've been notified and are working on fixing it.",
      "code": "internal_clerk_error"
    }
  ]
}
```

## Invitations

### <code><wbr />Invitation<wbr />Already<wbr />Accepted</code>

`InvitationAlreadyAccepted` denotes an error when someone tries to use
an invitation which is already accepted.

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Invitation is already accepted, try signing in instead.",
      "long_message": "Invitation is already accepted, try signing in instead.",
      "code": "invitation_already_accepted"
    }
  ]
}
```

### <code><wbr />Revoked<wbr />Invitation</code>

`RevokedInvitation` denotes an error when the given invitation token
does not correspond to any invitations, which means that the invitation
has been removed.

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "The invitation was revoked.",
      "long_message": "The invitation was revoked.",
      "code": "revoked_invitation"
    }
  ]
}
```

## JWT templates

### <code><wbr />J<wbr />W<wbr />T<wbr />Template<wbr />Not<wbr />Found</code>

`JWTTemplateNotFound` signifies an error when a JWT template was not found by the provided attribute

filename: Status Code: 404
```json
{
  "errors": [
    {
      "message": "JWT template not found",
      "long_message": "No JWT template exists with <attribute>: <val>",
      "code": "resource_not_found"
    }
  ]
}
```

### <code><wbr />J<wbr />W<wbr />T<wbr />Template<wbr />Reserved<wbr />Claim</code>

`JWTTemplateReservedClaim` denotes an error when the provided template contains a reserved claim.

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "reserved claim used",
      "long_message": "You can't use the reserved claim: '<claim>'",
      "code": "jwt_template_reserved_claim",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Session<wbr />Token<wbr />Template<wbr />Not<wbr />Deletable</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "session token template cannot be deleted",
      "long_message": "This template cannot be deleted because it's a session token template",
      "code": "session_token_jwt_template"
    }
  ]
}
```

## Management

### <code><wbr />Duplicate<wbr />List<wbr />Items<wbr />Not<wbr />Allowed</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "duplicate list items not allowed",
      "long_message": "duplicate list items not allowed: <param>",
      "code": "duplicate_list_items_not_allowed"
    }
  ]
}
```

### <code><wbr />Invalid<wbr />Environment<wbr />Type</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "invalid environment type",
      "long_message": "invalid environment types: <envTypes>",
      "code": "invalid_environment_type"
    }
  ]
}
```

### <code><wbr />Too<wbr />Many<wbr />Secret<wbr />Keys</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "too many secret keys",
      "long_message": "You can only rotate secret keys when your instance has exactly one key.",
      "code": "too_many_secret_keys"
    }
  ]
}
```

## Network

### <code><wbr />Gateway<wbr />Timeout</code>

`GatewayTimeout` signifies an error when a 3rd party service takes too long to respond.

filename: Status Code: 504
```json
{
  "errors": [
    {
      "message": "Gateway Timeout",
      "long_message": "A request to a 3rd party service timed out",
      "code": "gateway_timeout"
    }
  ]
}
```

## OAuth

### <code><wbr />Custom<wbr />O<wbr />Auth<wbr />Provider<wbr />Cannot<wbr />Delete<wbr />Active</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "active custom OAuth provider cannot be deleted",
      "long_message": "The custom OAuth provider \"<providerName>\" is currently active and cannot be deleted. You can disable it instead.",
      "code": "custom_oauth_provider_cannot_delete_active"
    }
  ]
}
```

### <code><wbr />Custom<wbr />O<wbr />Auth<wbr />Provider<wbr />Cannot<wbr />Use<wbr />Discovery<wbr />U<wbr />R<wbr />L</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "custom OAuth provider cannot use discovery URL",
      "long_message": "The custom OAuth provider cannot use the discovery URL. Please provide the necessary configuration manually.",
      "code": "custom_oauth_provider_cannot_use_discovery_url",
      "meta": {
        "param_name": "discovery_url"
      }
    }
  ]
}
```

### <code><wbr />Custom<wbr />O<wbr />Auth<wbr />Provider<wbr />Discovery<wbr />Issuer<wbr />Mismatch</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "issuer mismatch in custom OAuth provider discovery URL",
      "long_message": "The issuer in the discovery URL (<url>) does not match the issuer returned in the configuration (<issuer>).",
      "code": "custom_oauth_provider_discovery_issuer_mismatch",
      "meta": {
        "param_name": "discovery_url"
      }
    }
  ]
}
```

### <code><wbr />Custom<wbr />Oauth<wbr />Provider<wbr />Discovery<wbr />Server<wbr />Retrieval<wbr />Error</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "error retrieving OAuth response from provider's discovery URL",
      "long_message": "An error was encountered when attempting to retrieve metadata from the oauth url \"<url>\": \"<reason>\"",
      "code": "custom_oauth_provider_discovery_server_retrieval_error",
      "meta": {
        "param_name": "discovery_url"
      }
    }
  ]
}
```

### <code><wbr />Unsupported<wbr />Oauth<wbr />Provider</code>

`UnsupportedOauthProvider` signifies an error when an instance tries to enable
an OAuth external provider which is not supported.

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "<providerTitle> OAuth is not supported.",
      "long_message": "<providerTitle> OAuth is not supported. Please contact us if you think this error should not appear.",
      "code": "oauth_unsupported_provider"
    }
  ]
}
```

## Organizations

### <code><wbr />Already<wbr />A<wbr />Member<wbr />Of<wbr />Organization</code>

400 - User with given identifier is already a member of the
organization and cannot be added again

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "already a member",
      "long_message": "<user> is already a member of the organization.",
      "code": "already_a_member_in_organization"
    }
  ]
}
```

### <code><wbr />Exclusive<wbr />Organization<wbr />Membership</code>

422 - Returned when a user cannot join (or be added to) an organization
because either the user already belongs to an exclusive organization or the
target organization is exclusive and the user has other memberships.

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "exclusive organization membership",
      "long_message": "User cannot belong to multiple organizations because exclusive membership is enabled.",
      "code": "exclusive_organization_membership"
    }
  ]
}
```

### <code><wbr />Exclusive<wbr />Organization<wbr />Membership<wbr />Existing<wbr />Members</code>

422 - Returned when enabling exclusive\_membership on an organization is
rejected because the organization already has members who belong to other
organizations in the same instance. Enabling the flag would retroactively
violate the invariant for those pre-existing members, so the flip is denied.

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "exclusive organization membership cannot be enabled",
      "long_message": "Exclusive membership cannot be enabled because existing members of this organization belong to other organizations. Remove their other memberships before enabling exclusive membership.",
      "code": "exclusive_organization_membership_existing_members"
    }
  ]
}
```

### <code><wbr />Force<wbr />Organization<wbr />Selection<wbr />Not<wbr />Allowed<wbr />When<wbr />Organizations<wbr />Disabled</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "not allowed",
      "long_message": "`force_organization_selection` cannot be enabled when organizations are disabled. Please enable organizations first.",
      "code": "force_organization_selection_not_allowed_when_organizations_disabled"
    }
  ]
}
```

### <code><wbr />Organization<wbr />Member<wbr />Limit<wbr />Managed<wbr />By<wbr />Billing</code>

`OrganizationMemberLimitManagedByBilling` returns an error when trying to update
the member limit for an organization that is on a seat-based billing plan

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "member limit managed by Billing",
      "long_message": "This organization's member limit is managed by their subscription. It cannot be edited directly.",
      "code": "organization_member_limit_managed_by_billing",
      "meta": {
        "param_name": "max_allowed_memberships"
      }
    }
  ]
}
```

### <code><wbr />Organization<wbr />Membership<wbr />Quota<wbr />Exceeded</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "organization membership quota exceeded",
      "long_message": "You have reached your limit of <maxAllowed> organization memberships, including outstanding invitations.",
      "code": "organization_membership_quota_exceeded"
    }
  ]
}
```

### <code><wbr />Organization<wbr />Missing<wbr />Creator<wbr />Role<wbr />Permissions</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "missing permissions for creator role",
      "long_message": "The creator role must contain the following permissions: <permissionKeys>",
      "code": "organization_missing_creator_role_permissions"
    }
  ]
}
```

### <code><wbr />Organization<wbr />Name<wbr />Invalid</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "invalid organization name",
      "long_message": "The organization name \"<name>\" is invalid: <reason>",
      "code": "form_param_value_invalid",
      "meta": {
        "param_name": "name"
      }
    }
  ]
}
```

### <code><wbr />Organization<wbr />Not<wbr />Enabled<wbr />In<wbr />Instance</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "access denied",
      "long_message": "The organizations feature is not enabled for this instance. You can enable it at https://dashboard.clerk.com.",
      "code": "organization_not_enabled_in_instance"
    }
  ]
}
```

### <code><wbr />Organization<wbr />Not<wbr />Found</code>

404 - Organization not found
WARNING: This is safe to use for endpoints where the caller is authorized to be
aware of every organization. But if the endpoint errors if the caller is not
authorized on the organization, do not use this, because it leaks the existence
of the organization! Use `OrganizationNotFound`OrUnauthorized instead.

filename: Status Code: 404
```json
{
  "errors": [
    {
      "message": "not found",
      "long_message": "Given organization not found.",
      "code": "resource_not_found"
    }
  ]
}
```

### <code><wbr />Organization<wbr />Quota<wbr />Exceeded</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "organization quota exceeded",
      "long_message": "You have reached your limit of <maxAllowed> organizations. You can remove the organization limit by upgrading to a paid plan or using a production instance.",
      "code": "organization_quota_exceeded"
    }
  ]
}
```

### <code><wbr />Organization<wbr />Role<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "errors": [
    {
      "message": "not found",
      "long_message": "Organization role not found",
      "code": "resource_not_found",
      "meta": {
        "param_name": "<paramName>"
      }
    }
  ]
}
```

### <code><wbr />Organization<wbr />Role<wbr />On<wbr />Set<wbr />Assigned<wbr />To<wbr />User</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "role is assigned to users",
      "long_message": "The role <roleKey> is assigned to one or more users. Please re-assign the role to the users to proceed.",
      "code": "organization_role_on_set_assigned_to_user",
      "meta": {
        "role_key": "<roleKey>"
      }
    }
  ]
}
```

### <code><wbr />Organization<wbr />Role<wbr />Set<wbr />Reassignment<wbr />Contact<wbr />Support</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "contact support",
      "long_message": "This reassignment affects <affectedCount> memberships, contact support to complete this operation",
      "code": "organization_role_set_reassignment_contact_support"
    }
  ]
}
```

### <code><wbr />Organization<wbr />Role<wbr />Set<wbr />Reassignment<wbr />Mappings<wbr />Invalid</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "reassignment mappings invalid",
      "long_message": "The role <roleKey> is invalid in the reassignment mappings. It must be present in the new role set.",
      "code": "organization_role_set_reassignment_mappings_invalid",
      "meta": {
        "role_key": "<roleKey>"
      }
    }
  ]
}
```

### <code><wbr />Organization<wbr />Role<wbr />Set<wbr />Reassignment<wbr />Mappings<wbr />Missing</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "reassignment mappings missing",
      "long_message": "The following roles are missing from the reassignment mappings: <strings.Join(roleKeys, \", \")>",
      "code": "organization_role_set_reassignment_mappings_missing",
      "meta": {
        "role_keys": [
          "<roleKeys>"
        ]
      }
    }
  ]
}
```

### <code><wbr />Organizations<wbr />Disable<wbr />Not<wbr />Allowed</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "cannot disable organizations",
      "long_message": "Cannot disable organizations because <reason>.",
      "code": "organizations_disable_not_allowed"
    }
  ]
}
```

### <code><wbr />Organization<wbr />Slugs<wbr />Disabled</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "organization slugs not enabled",
      "long_message": "This instance does not have slugs enabled for organizations.",
      "code": "organization_slugs_disabled"
    }
  ]
}
```

### <code><wbr />Organization<wbr />Too<wbr />Large</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Organization too large",
      "long_message": "Organization size is above the API limit",
      "code": "organization_too_large",
      "meta": {
        "param_name": "organization_id"
      }
    }
  ]
}
```

### <code><wbr />Org<wbr />Creation<wbr />Limit<wbr />Exceeded<wbr />Error</code>

403 - Organization Creation Limit Exceeded

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "Organization Creation Limit Exceeded",
      "long_message": "You have exceeded the maximum number of organizations you can create.",
      "code": "org_creation_limit_exceeded"
    }
  ]
}
```

### <code><wbr />Role<wbr />Migration<wbr />In<wbr />Progress</code>

filename: Status Code: 409
```json
{
  "errors": [
    {
      "message": "migration in progress",
      "long_message": "Cannot modify role set while role reassignment is in progress. Please wait for the migration to complete.",
      "code": "role_migration_in_progress"
    }
  ]
}
```

## Platform

### <code><wbr />Domain<wbr />Intent<wbr />Canceled</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Domain intent is canceled",
      "long_message": "The provided domain intent is canceled.",
      "code": "domain_intent_canceled"
    }
  ]
}
```

### <code><wbr />Domain<wbr />Intent<wbr />Completed</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Domain intent is completed",
      "long_message": "The provided domain intent is already completed.",
      "code": "domain_intent_completed"
    }
  ]
}
```

### <code><wbr />Domain<wbr />Intent<wbr />Disallowed<wbr />Domain<wbr />Name</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "",
      "long_message": "",
      "code": "domain_intent_disallowed_domain_name"
    }
  ]
}
```

### <code><wbr />Domain<wbr />Intent<wbr />D<wbr />N<wbr />S<wbr />Requirements<wbr />Changed</code>

filename: Status Code: 409
```json
{
  "errors": [
    {
      "message": "Domain intent DNS requirements changed",
      "long_message": "The DNS requirements changed after this domain intent was created. Create a new domain intent and configure the newly issued records before trying again.",
      "code": "domain_intent_dns_requirements_changed"
    }
  ]
}
```

### <code><wbr />Domain<wbr />Intent<wbr />Invalid</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Domain intent is invalid",
      "long_message": "The provided domain intent is invalid.",
      "code": "domain_intent_invalid"
    }
  ]
}
```

### <code><wbr />Platform<wbr />A<wbr />P<wbr />I<wbr />Auth<wbr />Strategy<wbr />Not<wbr />Allowed</code>

`PlatformAPIAuthStrategyNotAllowed` signifies that the endpoint does not accept the authentication strategy used for the request.

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "Authentication method not allowed",
      "long_message": "This endpoint does not accept the credential type used. Use an authentication method allowed for this operation.",
      "code": "platform_api_auth_strategy_not_allowed"
    }
  ]
}
```

### <code><wbr />Platform<wbr />A<wbr />P<wbr />I<wbr />Policy<wbr />Violation</code>

`PlatformAPIPolicyViolation` signifies policy or issuer restrictions on OAuth access tokens for the Platform API (HTTP 403).

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "Authentication policy violation",
      "long_message": "This request cannot be completed due to a policy restriction.",
      "code": "authorization_invalid"
    }
  ]
}
```

### <code><wbr />Platform<wbr />A<wbr />P<wbr />I<wbr />Request<wbr />Not<wbr />Allowed</code>

`PlatformAPIRequestNotAllowed` signifies that the Platform API request is forbidden for the authenticated principal or target resource (HTTP 403).

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "Request not allowed",
      "long_message": "This Platform API request cannot be completed for the authenticated principal or resource.",
      "code": "authorization_invalid"
    }
  ]
}
```

### <code><wbr />Platform<wbr />A<wbr />P<wbr />I<wbr />Unrecognized<wbr />Credential</code>

`PlatformAPIUnrecognizedCredential` signifies that the bearer credential does not match any supported Platform API authentication format.

filename: Status Code: 401
```json
{
  "errors": [
    {
      "message": "Unrecognized credential",
      "long_message": "The credential format is not recognized for the Platform API.",
      "code": "platform_api_unrecognized_credential"
    }
  ]
}
```

### <code><wbr />Platform<wbr />O<wbr />Auth<wbr />Access<wbr />Token<wbr />Invalid</code>

`PlatformOAuthAccessTokenInvalid` signifies that an OAuth access token could not be parsed or verified.

filename: Status Code: 401
```json
{
  "errors": [
    {
      "message": "Invalid OAuth access token",
      "long_message": "The OAuth access token is invalid, malformed, or could not be verified.",
      "code": "platform_oauth_access_token_invalid"
    }
  ]
}
```

### <code><wbr />Platform<wbr />O<wbr />Auth<wbr />Access<wbr />Token<wbr />Missing<wbr />Claims</code>

`PlatformOAuthAccessTokenMissingClaims` signifies that a JWT access token is missing required claims.

filename: Status Code: 401
```json
{
  "errors": [
    {
      "message": "Invalid OAuth access token",
      "long_message": "Invalid OAuth access token",
      "code": "platform_oauth_access_token_missing_claims",
      "meta": {
        "claims": [
          "<cp>"
        ]
      }
    }
  ]
}
```

## Pricing

### <code><wbr />Unsupported<wbr />Subscription<wbr />Plan<wbr />Features</code>

filename: Status Code: 402
```json
{
  "errors": [
    {
      "message": "Unsupported plan features",
      "long_message": "Some features are not supported in your current plan. Upgrade your subscription to unlock them.",
      "code": "unsupported_subscription_plan_features",
      "meta": {
        "unsupported_features": [
          "<unsupportedFeatures>"
        ]
      }
    }
  ]
}
```

## Redirect URLs

### <code><wbr />Redirect<wbr />U<wbr />R<wbr />L<wbr />Not<wbr />Found</code>

`RedirectURLNotFound` signifies an error when a RedirectURL was not found by the provided attribute

filename: Status Code: 404
```json
{
  "errors": [
    {
      "message": "Redirect url not found",
      "long_message": "No RedirectURL exists with <attribute>: <val>",
      "code": "resource_not_found"
    }
  ]
}
```

## Requests

### <code><wbr />Invalid<wbr />J<wbr />S<wbr />O<wbr />N<wbr />Request<wbr />Body</code>

`InvalidJSONRequestBody` is a variant of [InvalidRequestBody] that returns a
more specific error message for malformed JSON.

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Request body invalid",
      "long_message": "Request body invalid",
      "code": "request_body_invalid"
    }
  ]
}
```

### <code><wbr />Invalid<wbr />Request<wbr />Body</code>

`InvalidRequestBody` signifies an error when the body of the request does not conform to the expected format

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Request body invalid",
      "long_message": "The request body is invalid. Please consult the API documentation for more information.",
      "code": "request_body_invalid"
    }
  ]
}
```

### <code><wbr />Request<wbr />Body<wbr />Too<wbr />Large</code>

filename: Status Code: 413
```json
{
  "errors": [
    {
      "message": "Request body too large",
      "long_message": "The request body exceeds the maximum allowed size of <maxBytes> bytes.",
      "code": "request_body_too_large"
    }
  ]
}
```

### <code><wbr />Unsupported<wbr />Content<wbr />Type</code>

`UnsupportedContentType` signifies an error when provided content type is unsupported

filename: Status Code: 415
```json
{
  "errors": [
    {
      "message": "Content-Type is unsupported",
      "long_message": "Content-Type <actual> is unsupported. You should use <expected> instead.",
      "code": "unsupported_content_type"
    }
  ]
}
```

## Sessions

### <code><wbr />Missing<wbr />Configurable<wbr />Session<wbr />Lifetime<wbr />Option</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Missing session lifetime settings",
      "long_message": "You must enable at least one of the session lifetime settings",
      "code": "session_lifetime_setting_missing"
    }
  ]
}
```

## Sign-up

### <code><wbr />Invalid<wbr />Value<wbr />For<wbr />Sign<wbr />Up<wbr />Mode</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "is not allowed",
      "long_message": "`<param>` isn't allowed to be `<value>` when sign-up mode is set to <mode>",
      "code": "sign_up_mode_restricted_invalid_value",
      "meta": {
        "param_name": "<param>"
      }
    }
  ]
}
```

### <code><wbr />Sign<wbr />Up<wbr />Mode<wbr />Invalid</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Invalid sign-up mode",
      "long_message": "The sign-up mode '<mode>' is invalid. Allowed values: <allowedModes>",
      "code": "sign_up_mode_invalid"
    }
  ]
}
```

## Subscription plans

### <code><wbr />Product<wbr />Not<wbr />Supported<wbr />By<wbr />Subscription<wbr />Plan</code>

filename: Status Code: 400
```json
{
  "errors": [
    {
      "message": "Product not supported by subscription plan",
      "long_message": "The product <productID> is not compatible with the current subscription plan",
      "code": "product_not_supported_by_subscription_plan"
    }
  ]
}
```

## TOTP

### <code><wbr />Invalid<wbr />T<wbr />O<wbr />T<wbr />P<wbr />Secret</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "invalid TOTP secret",
      "long_message": "The TOTP secret is invalid, please provide a valid one base32 encoded",
      "code": "invalid_totp_secret_code"
    }
  ]
}
```

## User settings

### <code><wbr />Attribute<wbr />At<wbr />Least<wbr />One<wbr />Must<wbr />Be<wbr />Verified<wbr />At<wbr />Sign<wbr />Up</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "at least one attribute must be verified on sign up",
      "long_message": "at least one attribute must be verified on sign up because <reason>",
      "code": "attribute_at_least_one_must_be_verified_at_sign_up"
    }
  ]
}
```

### <code><wbr />Resource<wbr />Forbidden</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "forbidden",
      "long_message": "Resource forbidden",
      "code": "resource_forbidden"
    }
  ]
}
```

### <code><wbr />Resource<wbr />Invalid</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "Resource invalid",
      "long_message": "Resource invalid",
      "code": "resource_invalid"
    }
  ]
}
```

### <code><wbr />Resource<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "errors": [
    {
      "message": "not found",
      "long_message": "Resource not found",
      "code": "resource_not_found"
    }
  ]
}
```

## Users

### <code><wbr />User<wbr />Data<wbr />Missing</code>

filename: Status Code: 422
```json
{
  "errors": [
    {
      "message": "missing data",
      "long_message": "\"<missingParams>\" data doesn't match user requirements set for this instance",
      "code": "form_data_missing",
      "meta": {
        "param_names": [
          "<missingParams>"
        ]
      }
    }
  ]
}
```

### <code><wbr />User<wbr />Not<wbr />Found</code>

`UserNotFound` signifies an error when no user is found with userID

filename: Status Code: 404
```json
{
  "errors": [
    {
      "message": "not found",
      "long_message": "No user was found with id <userID>",
      "code": "resource_not_found"
    }
  ]
}
```

### <code><wbr />User<wbr />Quota<wbr />Exceeded</code>

filename: Status Code: 403
```json
{
  "errors": [
    {
      "message": "user quota exceeded",
      "long_message": "You have reached your limit of <maxAllowed> users. <resolution>",
      "code": "user_quota_exceeded"
    }
  ]
}
```

### <code><wbr />User<wbr />S<wbr />C<wbr />I<wbr />M<wbr />Managed</code>

filename: Status Code: 409
```json
{
  "errors": [
    {
      "message": "user managed by directory sync",
      "long_message": "This user is managed by a directory and cannot be deleted manually.",
      "code": "user_managed_by_scim"
    }
  ]
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
