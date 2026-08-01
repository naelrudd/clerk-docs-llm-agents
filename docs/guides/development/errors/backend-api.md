# Backend API errors

An index of Clerk Backend API errors.

## Actor Tokens

### <code><wbr />Actor<wbr />Token<wbr />Cannot<wbr />Be<wbr />Revoked</code>

filename: Status Code: 400
```json
{
  "shortMessage": "cannot revoke",
  "longMessage": "Actor token cannot be revoked because its status is <status>. Only pending tokens can be revoked.",
  "code": "actor_token_cannot_be_revoked_code"
}
```

## Agent Tasks

### <code><wbr />Agent<wbr />Task<wbr />Cannot<wbr />Be<wbr />Revoked</code>

filename: Status Code: 400
```json
{
  "shortMessage": "cannot revoke agent task",
  "longMessage": "cannot revoke agent task",
  "code": "agent_task_cannot_be_revoked"
}
```

### <code><wbr />Agent<wbr />Task<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "agent task not found",
  "longMessage": "The requested agent task could not be found.",
  "code": "agent_task_not_found"
}
```

### <code><wbr />Agent<wbr />Task<wbr />Subject<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "user not found",
  "longMessage": "The user of the agent task no longer exists. Please request a new one.",
  "code": "agent_task_subject_not_found"
}
```

## Allowlist Identifiers

### <code><wbr />Allowlist<wbr />Identifier<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "Identifier not found",
  "longMessage": "No identifier was found with id <identifierID>",
  "code": "resource_not_found"
}
```

### <code><wbr />Duplicate<wbr />Allowlist<wbr />Identifier</code>

filename: Status Code: 400
```json
{
  "shortMessage": "duplicate allowlist identifier",
  "longMessage": "the identifier <identifier> already exists",
  "code": "duplicate_record"
}
```

## Apikeys

### <code><wbr />A<wbr />P<wbr />I<wbr />Keys<wbr />Not<wbr />Enabled</code>

filename: Status Code: 422
```json
{
  "shortMessage": "API Keys not enabled",
  "longMessage": "API Keys not enabled",
  "code": "api_keys_not_enabled"
}
```

## Applications

### <code><wbr />Accountless<wbr />Application<wbr />Not<wbr />Found</code>

`AccountlessApplicationNotFound` signifies an error when no application with the given claim token could be found

filename: Status Code: 404
```json
{
  "shortMessage": "Application not found",
  "longMessage": "No application was found with the given claim token.",
  "code": "resource_not_found"
}
```

### <code><wbr />Application<wbr />Already<wbr />Belongs<wbr />To<wbr />Organization</code>

filename: Status Code: 400
```json
{
  "shortMessage": "already belongs to organization",
  "longMessage": "Application already belongs to the selected organization.",
  "code": "application_already_belongs_to_organization"
}
```

### <code><wbr />Application<wbr />Not<wbr />Found</code>

`ApplicationNotFound` signifies an error when no application with the specified id was found

filename: Status Code: 404
```json
{
  "shortMessage": "Application not found",
  "longMessage": "No application was found with the specified id",
  "code": "resource_not_found"
}
```

### <code><wbr />Invalid<wbr />Application<wbr />Name</code>

filename: Status Code: 422
```json
{
  "shortMessage": "invalid application name",
  "longMessage": "The application name %q is invalid: <name>",
  "code": "form_param_value_invalid",
  "meta": {
    "name": "name"
  }
}
```

### <code><wbr />Workspace<wbr />Not<wbr />Configured</code>

`WorkspaceNotConfigured` is returned when the workspace is missing
configuration required to complete the operation (for example, a role
or feature that has not yet been provisioned).

filename: Status Code:&#x20;
```json
{
  "shortMessage": "workspace not configured",
  "longMessage": "Workspace is not configured for this operation.",
  "code": "workspace_not_configured"
}
```

## Auth

### <code><wbr />Could<wbr />Not<wbr />Authenticate<wbr />Request</code>

filename: Status Code: 401
```json
{
  "shortMessage": "Could not authenticate request.",
  "longMessage": "Could not authenticate request.",
  "code": "could_not_authenticate_request"
}
```

### <code><wbr />Identification<wbr />Exists</code>

`IdentificationExists` signifies an error when the identifier already exists

filename: Status Code: 400
```json
{
  "shortMessage": "already exists",
  "longMessage": "This <identifier> already exists.",
  "code": ""
}
```

### <code><wbr />Identifier<wbr />Not<wbr />Allowed<wbr />Access</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Access not allowed.",
  "longMessage": "<who> <pluralization> not allowed to access this application.",
  "code": "not_allowed_access",
  "meta": "{\"Identifiers\": identifiers}"
}
```

### <code><wbr />Invalid<wbr />Authentication</code>

`InvalidAuthentication` signifies an error when the request is not authenticated

filename: Status Code: 401
```json
{
  "shortMessage": "Invalid authentication",
  "longMessage": "Unable to authenticate the request, you need to supply an active session",
  "code": "authentication_invalid"
}
```

### <code><wbr />Invalid<wbr />Authorization</code>

`InvalidAuthorization` signifies an error when the request is not authorized to perform the given operation

filename: Status Code: 403
```json
{
  "shortMessage": "Unauthorized request",
  "longMessage": "You are not authorized to perform this request",
  "code": "authorization_invalid"
}
```

### <code><wbr />Invalid<wbr />Authorization<wbr />Header<wbr />Format</code>

`InvalidAuthorizationHeaderFormat` signifies an error when the Authorization header has no proper format.

filename: Status Code: 401
```json
{
  "shortMessage": "Invalid Authorization header format",
  "longMessage": "Invalid Authorization header format. Must be 'Bearer <YOUR_API_KEY>'",
  "code": "authorization_header_format_invalid"
}
```

### <code><wbr />Invalid<wbr />Clerk<wbr />Secret<wbr />Key</code>

`InvalidClerkSecretKey` signifies an error when the supplied client key is invalid

filename: Status Code: 401
```json
{
  "shortMessage": "The provided Clerk Secret Key is invalid. Make sure that your Clerk Secret Key is correct.",
  "longMessage": "The provided Clerk Secret Key is invalid. Make sure that your Clerk Secret Key is correct.",
  "code": "clerk_key_invalid"
}
```

### <code><wbr />Invalid<wbr />Request<wbr />For<wbr />Environment</code>

`InvalidRequestForEnvironment` signifies an error when the incoming request is invalid for given environment(s)

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid request for environment",
  "longMessage": "Request only valid for <envTypes> instances.",
  "code": "request_invalid_for_environment"
}
```

### <code><wbr />Invalid<wbr />User<wbr />Settings</code>

`InvalidUserSettings` signifies an error where the auth settings of the instance
are not well configured, which results in sign in and sign up endpoints to be
restricted.

filename: Status Code: 409
```json
{
  "shortMessage": "invalid auth configuration",
  "longMessage": "The authentication settings are invalid.",
  "code": "user_settings_invalid"
}
```

### <code><wbr />Request<wbr />Invalid<wbr />For<wbr />Instance</code>

`RequestInvalidForInstance` signifies an error when the incoming request is invalid for the given instance, due to the auth\_config

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid request for instance",
  "longMessage": "This request is not valid for your instance. Modify your instance settings to use this request.",
  "code": "request_invalid_for_instance"
}
```

### <code><wbr />Subaddress<wbr />Restriction<wbr />Email<wbr />Already<wbr />Used</code>

filename: Status Code: 403
```json
{
  "shortMessage": "This email address is already in use.",
  "longMessage": "This email address is already in use. Creating multiple accounts with the same email address is not allowed.",
  "code": "not_allowed_access"
}
```

### <code><wbr />Unsupported<wbr />Country</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Unsupported country code",
  "longMessage": "Phone numbers from this country (<countryName>) are currently not supported. For more information, please contact <support>.",
  "code": "unsupported_country_code",
  "meta": "{\"Alpha2\": alpha2, \"CountryCode\": countryCode}"
}
```

## Blocklist Identifiers

### <code><wbr />Blocklist<wbr />Identifier<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "Identifier not found",
  "longMessage": "No identifier was found with id <identifierID>",
  "code": "resource_not_found"
}
```

### <code><wbr />Duplicate<wbr />Blocklist<wbr />Identifier</code>

filename: Status Code: 400
```json
{
  "shortMessage": "duplicate blocklist identifier",
  "longMessage": "the identifier <identifier> already exists",
  "code": "duplicate_record"
}
```

## Clients

### <code><wbr />Client<wbr />Not<wbr />Found</code>

`ClientNotFound` signifies an error when no client is found with clientID

filename: Status Code: 404
```json
{
  "shortMessage": "Client not found",
  "longMessage": "No client was found with id <clientID>",
  "code": "resource_not_found"
}
```

### <code><wbr />Client<wbr />Not<wbr />Found<wbr />In<wbr />Request</code>

`ClientNotFoundInRequest` signifies an error when no client is found in an incoming request

filename: Status Code: 400
```json
{
  "shortMessage": "No client found",
  "longMessage": "This request is expecting a client and did not find one",
  "code": "client_not_found"
}
```

## Commerce

### <code><wbr />Billing<wbr />Annual<wbr />Only<wbr />Plans<wbr />Not<wbr />Enabled</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Annual only plans are not enabled",
  "longMessage": "Annual only plans are not enabled, please enable the update in Clerk dashboard.",
  "code": "billing_annual_only_plans_not_enabled"
}
```

### <code><wbr />Billing<wbr />Cannot<wbr />Be<wbr />Disabled</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Cannot disable Billing",
  "longMessage": "Cannot disable Billing because <reason>.",
  "code": "billing_cannot_be_disabled"
}
```

### <code><wbr />Billing<wbr />Cannot<wbr />Be<wbr />Enabled</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Cannot enable Billing",
  "longMessage": "Cannot enable Billing because <reason>.",
  "code": "billing_cannot_be_enabled"
}
```

### <code><wbr />Billing<wbr />Not<wbr />Enabled<wbr />For<wbr />Org</code>

filename: Status Code: 403
```json
{
  "shortMessage": "access denied",
  "longMessage": "The billing feature for organizations is not enabled for this instance. You can enable it at https://dashboard.clerk.com.",
  "code": "billing_not_enabled"
}
```

### <code><wbr />Billing<wbr />Not<wbr />Enabled<wbr />For<wbr />User</code>

filename: Status Code: 403
```json
{
  "shortMessage": "access denied",
  "longMessage": "The billing feature for users is not enabled for this instance. You can enable it at https://dashboard.clerk.com.",
  "code": "billing_not_enabled"
}
```

### <code><wbr />Billing<wbr />Too<wbr />Few<wbr />Free<wbr />Trial<wbr />Days</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid free trial days",
  "longMessage": "Free trial days must be at least 1 day",
  "code": "billing_too_few_free_trial_days"
}
```

### <code><wbr />Billing<wbr />Too<wbr />Many<wbr />Free<wbr />Trial<wbr />Days</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid free trial days",
  "longMessage": "Free trial days must be at most 365 days",
  "code": "billing_too_many_free_trial_days"
}
```

### <code><wbr />Checkout<wbr />Already<wbr />In<wbr />Progress</code>

filename: Status Code: 409
```json
{
  "shortMessage": "Another checkout is already in progress",
  "longMessage": "Another checkout is already in progress",
  "code": "checkout_already_in_progress"
}
```

### <code><wbr />Commerce<wbr />Insufficient<wbr />Seats</code>

filename: Status Code: 402
```json
{
  "shortMessage": "Insufficient seats",
  "longMessage": "You have reached the seat limit for your current plan.",
  "code": "insufficient_seats",
  "meta": {
    "seatsquantity": "totalneeded"
  }
}
```

### <code><wbr />Currency<wbr />Invalid</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid currency",
  "longMessage": "Currency is not supported",
  "code": "currency_invalid"
}
```

### <code><wbr />Default<wbr />Plan<wbr />Amount<wbr />Update<wbr />Forbidden</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Default plan amount update forbidden",
  "longMessage": "Default plan pricing cannot be modified. Only paid plans support amount updates",
  "code": "default_plan_amount_update_forbidden"
}
```

### <code><wbr />Free<wbr />Trial<wbr />Not<wbr />Allowed<wbr />On<wbr />Free<wbr />Plan</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Free trial not allowed on free plan",
  "longMessage": "Free trials cannot be enabled on free plans",
  "code": "free_trial_not_allowed_on_free_plan"
}
```

### <code><wbr />Invalid<wbr />Credit<wbr />Action</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Invalid credit action",
  "longMessage": "Credit action must be either 'increase' or 'decrease'",
  "code": "invalid_credit_action"
}
```

### <code><wbr />Invalid<wbr />Credit<wbr />Amount</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Invalid credit amount",
  "longMessage": "Credit amount must be greater than zero",
  "code": "invalid_credit_amount"
}
```

### <code><wbr />Missing<wbr />Name</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Missing name",
  "longMessage": "Name is required to perform this operation",
  "code": "missing_name"
}
```

### <code><wbr />Missing<wbr />Slug</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Missing slug",
  "longMessage": "Slug is required to perform this operation",
  "code": "missing_slug"
}
```

### <code><wbr />Name<wbr />Invalid<wbr />Format</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid  name format",
  "longMessage": "Name cannot contain colons (:)",
  "code": "name_invalid_format",
  "meta": {
    "name": "name"
  }
}
```

### <code><wbr />Name<wbr />Invalid<wbr />Length</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Name length is invalid",
  "longMessage": "Name must be between %d and %d characters",
  "code": "name_invalid_length",
  "meta": {
    "name": "name"
  }
}
```

### <code><wbr />Payee<wbr />Not<wbr />Active</code>

filename: Status Code: 409
```json
{
  "shortMessage": "Payee not active",
  "longMessage": "Payee is not active",
  "code": "payee_not_active"
}
```

### <code><wbr />Payee<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "Payee not found",
  "longMessage": "Payee not found",
  "code": "payee_not_found"
}
```

### <code><wbr />Payee<wbr />Status<wbr />Invalid</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Payee status is invalid",
  "longMessage": "Payee status is invalid",
  "code": "payee_status_invalid"
}
```

### <code><wbr />Payer<wbr />Credits<wbr />Disabled</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Payer credits disabled",
  "longMessage": "The payer credits feature is not enabled for this application",
  "code": "payer_credits_disabled"
}
```

### <code><wbr />Payer<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "Payer not found",
  "longMessage": "Payer not found",
  "code": "payer_not_found"
}
```

### <code><wbr />Payer<wbr />Type<wbr />Invalid</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid payer type",
  "longMessage": "Payer type is invalid",
  "code": "payer_type_invalid"
}
```

### <code><wbr />Payment<wbr />Attempt<wbr />Failed<wbr />Requires<wbr />Confirmation</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Requires confirmation",
  "longMessage": "The payment attempt failed because it requires additional confirmation, which is not currently supported. Please use a different payment method.",
  "code": "payment_attempt_failed_requires_confirmation"
}
```

### <code><wbr />Payment<wbr />Declined</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Your card was declined",
  "longMessage": "The card was declined.",
  "code": "payment_attempt_failed_card_declined"
}
```

### <code><wbr />Payment<wbr />Expired<wbr />Card</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Card expired",
  "longMessage": "The card has expired.",
  "code": "payment_attempt_failed_card_expired"
}
```

### <code><wbr />Payment<wbr />Insufficient<wbr />Funds</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Insufficient funds",
  "longMessage": "The card has insufficient funds.",
  "code": "payment_attempt_failed_card_insufficient_funds"
}
```

### <code><wbr />Payment<wbr />Processing<wbr />Error</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Processing error",
  "longMessage": "There was a processing error with the payment method.",
  "code": "payment_attempt_failed_processing_error"
}
```

### <code><wbr />Plan<wbr />Amount<wbr />Invalid</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Paid plan month or annual fee invalid",
  "longMessage": "Paid plan month or annual fee invalid",
  "code": "plan_amount_invalid"
}
```

### <code><wbr />Plan<wbr />Amount<wbr />Too<wbr />Large</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Paid plan monthly base fee exceeds upper limit",
  "longMessage": "Paid plan monthly base fee must be less than $999,999.99",
  "code": "plan_amount_exceeds_upper_limit"
}
```

### <code><wbr />Plan<wbr />Cannot<wbr />Be<wbr />Deleted</code>

filename: Status Code: 409
```json
{
  "shortMessage": "Plan cannot be deleted",
  "longMessage": "This plan cannot be deleted because <reason>.",
  "code": "plan_cannot_be_deleted"
}
```

### <code><wbr />Plan<wbr />Free<wbr />Trials<wbr />Disabled</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Free trials disabled",
  "longMessage": "Free trials are disabled for this plan",
  "code": "plan_free_trials_disabled"
}
```

### <code><wbr />Plan<wbr />Name<wbr />Already<wbr />Exists</code>

filename: Status Code: 409
```json
{
  "shortMessage": "Plan name already exists",
  "longMessage": "Plan name already exists",
  "code": "plan_name_already_exists",
  "meta": {
    "name": "name"
  }
}
```

### <code><wbr />Plan<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "Plan not found",
  "longMessage": "Plan not found",
  "code": "plan_not_found"
}
```

### <code><wbr />Product<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "Product not found",
  "longMessage": "Product not found",
  "code": "product_not_found"
}
```

### <code><wbr />Slug<wbr />Invalid<wbr />Format</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid slug format",
  "longMessage": "Slug must only use letters, numbers, dashes (-), and underscores (_). Colons and other characters are not allowed.",
  "code": "slug_invalid_format",
  "meta": {
    "name": "slug"
  }
}
```

### <code><wbr />Slug<wbr />Invalid<wbr />Length</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Slug length is invalid",
  "longMessage": "Slug must be between %d and %d characters",
  "code": "slug_invalid_length",
  "meta": {
    "name": "slug"
  }
}
```

### <code><wbr />Subscription<wbr />Item<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "Subscription item not found",
  "longMessage": "Subscription item not found",
  "code": "subscription_item_not_found"
}
```

### <code><wbr />Subscription<wbr />Item<wbr />Not<wbr />In<wbr />Free<wbr />Trial</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Subscription item is not in free trial",
  "longMessage": "Subscription item is not in free trial",
  "code": "subscription_item_not_in_free_trial"
}
```

## Config

### <code><wbr />Config<wbr />Validation<wbr />Error</code>

`ConfigValidationError` returns a 422 error with schema path

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "config_validation_error",
  "meta": {
    "config_key": "configkey",
    "param_name": "paramname",
    "schema_path": "schemapath"
  }
}
```

### <code><wbr />Config<wbr />Version<wbr />Conflict</code>

`ConfigVersionConflict` returns a 409 error for ETag mismatch

filename: Status Code: 409
```json
{
  "shortMessage": "Config version conflict",
  "longMessage": "Config was modified since last read. Re-fetch and retry.",
  "code": "config_version_conflict",
  "meta": {
    "current_version": "currentversion",
    "provided_version": "providedversion"
  }
}
```

### <code><wbr />Destructive<wbr />Operation<wbr />Not<wbr />Allowed</code>

`DestructiveOperationNotAllowed` returns a 400 error

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "Cannot clear config key '<key>' without destructive=true",
  "code": "destructive_operation_not_allowed",
  "meta": {
    "param_name": "key"
  }
}
```

### <code><wbr />Invalid<wbr />Config<wbr />Key<wbr />Body</code>

`InvalidConfigKeyBody` returns a 400 error indicating the value for a config
key has the wrong shape (e.g. an array of objects where the schema expects
an array of strings).

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "The value for config key '<key>' does not match the expected schema.",
  "code": "config_key_body_invalid",
  "meta": {
    "param_name": "key"
  }
}
```

### <code><wbr />Missing<wbr />Config<wbr />Keys</code>

`MissingConfigKeys` returns a 400 error listing keys that were not included in a PUT request

filename: Status Code: 400
```json
{
  "shortMessage": "Missing config keys",
  "longMessage": "PUT requires all config keys to be included. Some keys are missing.",
  "code": "missing_config_keys",
  "meta": {
    "missingkeys": "missing"
  }
}
```

### <code><wbr />Unknown<wbr />Config<wbr />Key</code>

`UnknownConfigKey` returns a 400 error with typo suggestions

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "Unknown config key '<key>'",
  "code": "unknown_config_key",
  "meta": "meta"
}
```

## Cookie

### <code><wbr />Invalid<wbr />Cookie</code>

`InvalidCookie` signifies an error when cookie is invalid

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "code": "cookie_invalid"
}
```

### <code><wbr />Invalid<wbr />Rotating<wbr />Token</code>

`InvalidRotatingToken` signifies an error when rotating token does not match the client's rotating token

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "The client's rotating key does not match the given one <token>",
  "code": "cookie_invalid"
}
```

### <code><wbr />Missing<wbr />Claims</code>

`MissingClaims` signifies an error when token is missing claim

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "The token is missing the following claims: <claims>",
  "code": "cookie_invalid"
}
```

## Deprecation

### <code><wbr />A<wbr />P<wbr />I<wbr />Endpoint<wbr />Deprecated</code>

filename: Status Code: 410
```json
{
  "shortMessage": "endpoint is deprecated and pending removal",
  "longMessage": "endpoint is deprecated and pending removal",
  "code": "operation_deprecated"
}
```

## Domains

### <code><wbr />Domain<wbr />Update<wbr />Forbidden</code>

`DomainUpdateForbidden` signifies an error when trying to update an non production instance domain

filename: Status Code: 400
```json
{
  "shortMessage": "Domain update was forbidden",
  "longMessage": "Domain can be only updated for production instances",
  "code": "domain_update_forbidden"
}
```

### <code><wbr />Feature<wbr />Requires<wbr />Custom<wbr />Domain</code>

`FeatureRequiresCustomDomain` signifies an error when a feature is blocked
because the instance only has a provider domain (e.g. vercel.app).

filename: Status Code: 403
```json
{
  "shortMessage": "custom domain required",
  "longMessage": "<feature> requires a custom domain. Add a custom domain to unlock this feature.",
  "code": "feature_requires_custom_domain"
}
```

### <code><wbr />Invalid<wbr />Proxy<wbr />Configuration</code>

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "longMessage": "Clerk Frontend API cannot be accessed through the proxy URL. Make sure your proxy is configured correctly.",
  "code": "invalid_proxy_configuration",
  "meta": {
    "name": "proxy_url"
  }
}
```

### <code><wbr />Operation<wbr />Not<wbr />Allowed<wbr />On<wbr />Primary<wbr />Domain</code>

filename: Status Code: 403
```json
{
  "shortMessage": "operation not allowed",
  "longMessage": "This operation is not allowed on a primary domain. Try again with a satellite domain of the instance.",
  "code": "operation_not_allowed_on_primary_domain"
}
```

### <code><wbr />Primary<wbr />Domain<wbr />Already<wbr />Exists</code>

`PrimaryDomainAlreadyExists` signifies an error when a new domain is added as
primary when there is already once in the instance.
Currently, we only support a single primary domain per instance.

filename: Status Code: 422
```json
{
  "shortMessage": "primary domain already exists",
  "longMessage": "Currently, only a single primary domain is supported and the current instance already has one. All new domains need to be set a satellites.",
  "code": "primary_domain_already_exists",
  "meta": {
    "name": "is_satellite"
  }
}
```

### <code><wbr />Provider<wbr />Domain<wbr />Operation<wbr />Not<wbr />Allowed<wbr />For<wbr />A<wbr />P<wbr />I</code>

Return this error when an API other than Platform API is used to create/update/delete a provider domain.

filename: Status Code: 403
```json
{
  "shortMessage": "operation not allowed",
  "longMessage": "*<provider> domains are not supported for production instances. Please purchase a domain then try again.",
  "code": "provider_domain_operation_not_allowed"
}
```

### <code><wbr />Proxy<wbr />U<wbr />R<wbr />L<wbr />Required<wbr />For<wbr />Provider<wbr />Domain</code>

`ProxyURLRequiredForProviderDomain` signifies an error when a provider domain
(e.g., replit.app, vercel.app) is created without a proxy URL.

filename: Status Code: 422
```json
{
  "shortMessage": "proxy URL required",
  "longMessage": "Provider domain <domainName> requires a proxy URL. Provider domains must be configured with a proxy.",
  "code": "proxy_url_required_for_provider_domain",
  "meta": {
    "name": "paramname"
  }
}
```

## Email

### <code><wbr />Dev<wbr />Monthly<wbr />Email<wbr />Limit<wbr />Exceeded</code>

`DevMonthlyEmailLimitExceeded` signifies an error when an email sending attempt is made while the development limit has already been reached

filename: Status Code: 400
```json
{
  "shortMessage": "Development monthly email limit exceeded",
  "longMessage": "The monthly limit for email messages in development (%d) has been reached. Please use test emails (https://go.clerk.com/test-emails) instead",
  "code": "dev_monthly_email_limit_exceeded",
  "meta": "{\"DevMonthlyEmailLimit\": limit}"
}
```

## Features

### <code><wbr />Feature<wbr />In<wbr />Use</code>

filename: Status Code: 409
```json
{
  "shortMessage": "Feature in use",
  "longMessage": "Feature is in use",
  "code": "feature_in_use"
}
```

### <code><wbr />Feature<wbr />Not<wbr />Enabled</code>

filename: Status Code: 403
```json
{
  "shortMessage": "not enabled",
  "longMessage": "This feature is not enabled on this instance",
  "code": "feature_not_enabled"
}
```

### <code><wbr />Feature<wbr />Not<wbr />Enabled<wbr />With<wbr />Meta</code>

filename: Status Code: 403
```json
{
  "shortMessage": "not enabled",
  "longMessage": "This feature is not enabled on this instance",
  "code": "feature_not_enabled",
  "meta": {
    "name": "paramname"
  }
}
```

### <code><wbr />Feature<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "Feature not found",
  "longMessage": "Feature not found",
  "code": "feature_not_found"
}
```

### <code><wbr />Feature<wbr />Requires<wbr />O<wbr />I<wbr />D<wbr />C<wbr />Provider</code>

filename: Status Code: 422
```json
{
  "shortMessage": "not an OIDC provider",
  "longMessage": "You are using the legacy OAuth 2.0 provider. Please migrate to the new OIDC compatible provider to use this feature",
  "code": "feature_requires_oidc_provider"
}
```

### <code><wbr />Feature<wbr />Requires<wbr />P<wbr />S<wbr />U</code>

filename: Status Code: 422
```json
{
  "shortMessage": "not a Progressive Sign Up instance",
  "longMessage": "<feature> can only be used in instances that migrated to Progressive Sign Up. This feature is deprecated, please contact support if you need assistance.",
  "code": "feature_requires_progressive_sign_up"
}
```

### <code><wbr />Not<wbr />Implemented</code>

filename: Status Code: 403
```json
{
  "shortMessage": "not implemented",
  "longMessage": "Feature `<feature>` is not available yet",
  "code": "feature_not_implemented"
}
```

## Forms

### <code><wbr />Form<wbr />Already<wbr />Exists</code>

`FormAlreadyExists` signifies an error when given resource already exists

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_already_exists",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Already<wbr />Exists<wbr />By<wbr />Provider<wbr />Managed<wbr />Domain</code>

`FormAlreadyExistsByProviderManagedDomain` signifies an error when a domain
already exists on an app managed by an external provider.

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "longMessage": "The <domain> root domain is already in use by a <providerName> app. Delete the <providerName> app or contact <providerName> support to remove the domain before using it in Clerk.",
  "code": "form_already_exists",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />At<wbr />Least<wbr />One<wbr />Optional<wbr />Parameter<wbr />Missing</code>

`FormAtLeastOneOptionalParameterMissing` signifies an error when at least one optional parameter must be provided

filename: Status Code: 422
```json
{
  "shortMessage": "at least one parameter must be provided",
  "longMessage": "at least one of `<parameters>` must be provided",
  "code": "form_param_missing",
  "meta": {
    "names": "paramnames"
  }
}
```

### <code><wbr />Form<wbr />Disallow<wbr />Future<wbr />Date</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Date values must not be in the future.",
  "longMessage": "Date values must not be in the future.",
  "code": "form_disallow_future_date",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Duplicate<wbr />Parameter</code>

`FormDuplicateParameter` signifies an error when a duplicate parameter is found in a form

filename: Status Code: 422
```json
{
  "shortMessage": "is duplicate",
  "longMessage": "<param> included multiple times. There should only be one.",
  "code": "form_param_duplicate",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Duplicate<wbr />Parameter<wbr />Value</code>

`FormDuplicateParameterValue` signifies an error when a value has been provided multiple times

filename: Status Code: 422
```json
{
  "shortMessage": "duplicate values",
  "longMessage": "<value> contains duplicate values",
  "code": "form_param_duplicate",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Identifier<wbr />Exists</code>

`FormIdentifierExists` signifies an error when given identifier already exists

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_identifier_exists",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Identifier<wbr />Exists<wbr />With<wbr />Another<wbr />Account</code>

`FormIdentifierExistsWithAnotherAccount` signifies an error when given identifier already exists.
This is used to signal to a user that the identifier, phone number, is already associated with another account and should remove it from the other account.

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_identifier_exists",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Date</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Date values must be given in Unix millisecond timestamp format.",
  "longMessage": "Date values must be given in Unix millisecond timestamp format.",
  "code": "form_param_invalid_date",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Email<wbr />Address</code>

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "<parameter> must be a valid email address.",
  "code": "form_param_format_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Email<wbr />Local<wbr />Part</code>

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "<param> must be a valid email address local part.",
  "code": "form_param_format_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Encoding<wbr />Parameter<wbr />Value</code>

`FormInvalidEncodingParameterValue` signifies an error when the given parameter has an invalid encoding

filename: Status Code: 422
```json
{
  "shortMessage": "invalid character encoding",
  "longMessage": "<param> contains invalid UTF-8 characters",
  "code": "form_param_value_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Identifier</code>

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "<param> must be either a valid email address, a valid phone number according to E.164 international standard or a valid web3 wallet.",
  "code": "form_param_format_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Origin</code>

`FormInvalidOrigin` signifies an error when the given origin is http/https

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "<param> must be a valid origin such as my-app://localhost, chrome-extension://mnhbilbfebpbokpjjamapdecdgieldho, or capacitor://localhost:3000",
  "code": "form_invalid_origin",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Parameter<wbr />Format</code>

`FormInvalidParameterFormat` signifies an error when the given parameter has an invalid format

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_param_format_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Parameter<wbr />Format<wbr />B<wbr />C<wbr />P47</code>

`FormInvalidParameterFormatBCP47` signifies an error when the given parameter does not match the BCP-47 format

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "<parameter> must be a valid BCP-47 language tag.",
  "code": "form_param_format_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Parameter<wbr />Only<wbr />One<wbr />Of<wbr />Allowed</code>

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "<param> is invalid. Only one of the following parameter values is allowed: <allowedValues>",
  "code": "form_param_value_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Parameter<wbr />Value</code>

`FormInvalidParameterValue` signifies an error when the given parameter has an invalid value

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "<value> does not match one of the allowed values for parameter <param>",
  "code": "form_param_value_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Parameter<wbr />Value<wbr />Must<wbr />Be<wbr />Not<wbr />Empty</code>

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "<param> is invalid. Must be not empty",
  "code": "form_param_value_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Parameter<wbr />Value<wbr />With<wbr />Allowed</code>

`FormInvalidParameterValueWithAllowed` signifies an error when the given parameter has an invalid value.
The difference with FormInvalidParameterValue is that this error also includes the allowed values

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "<value> does not match the allowed values for parameter <param>. Allowed values: <allowedValues>",
  "code": "form_param_value_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />Length<wbr />Too<wbr />Long</code>

`FormInvalidPasswordLengthTooLong` signifies an error when the password is invalid because of its length

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_password_length_too_long",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />Length<wbr />Too<wbr />Short</code>

`FormInvalidPasswordLengthTooShort` signifies an error when the password is invalid because of its length

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_password_length_too_short",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />No<wbr />Lowercase</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Passwords must contain at least one lowercase character.",
  "longMessage": "Passwords must contain at least one lowercase character.",
  "code": "form_password_no_lowercase",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />No<wbr />Number</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Passwords must contain at least one number.",
  "longMessage": "Passwords must contain at least one number.",
  "code": "form_password_no_number",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />No<wbr />Special<wbr />Char</code>

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_password_no_special_char",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />Not<wbr />Strong<wbr />Enough</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Given password is not strong enough.",
  "longMessage": "Given password is not strong enough.",
  "code": "form_password_not_strong_enough"
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Password<wbr />No<wbr />Uppercase</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Passwords must contain at least one uppercase character.",
  "longMessage": "Passwords must contain at least one uppercase character.",
  "code": "form_password_no_uppercase",
  "meta": {
    "name": "param"
  }
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
  "shortMessage": "Your password is too long. Please use a shorter one.",
  "longMessage": "Your password is too long. Please use a shorter one.",
  "code": "form_password_size_in_bytes_exceeded",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Phone<wbr />Number</code>

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "<parameter> must be a valid phone number according to E.164 international standard.",
  "code": "form_param_format_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Time</code>

filename: Status Code: 422
```json
{
  "shortMessage": "invalid format",
  "longMessage": "<param> must contain a datetime specified in RFC3339 format (e.g. `2022-10-20T10:00:27.645Z`).",
  "code": "form_param_invalid_time",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Type<wbr />Parameter</code>

`FormInvalidTypeParameter` signifies an error when a form parameter has the wrong type

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "`<param>` must be a `<paramType>`.",
  "code": "form_param_type_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Username<wbr />Character</code>

`FormInvalidUsernameCharacter` signifies an error when the given username does not match username regex

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_username_invalid_character",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Username<wbr />Length</code>

`FormInvalidUsernameLength` signifies an error when the given username does not have required length

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_username_invalid_length",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Username<wbr />Needs<wbr />Non<wbr />Number<wbr />Char<wbr />Code</code>

`FormInvalidUsernameNeedsNonNumberCharCode` signifies an error when the given username does not match username regex

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_username_needs_non_number_char",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Invalid<wbr />Web3<wbr />Wallet<wbr />Address</code>

`FormInvalidWeb3WalletAddress` signifies an error when the given web3 wallet address is invalid

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "<parameter> must be a valid web3 wallet address.",
  "code": "form_param_format_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Metadata<wbr />Invalid<wbr />Type</code>

`FormMetadataInvalidType` signifies an error when the given metadata is not a valid key-value object

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_param_value_invalid",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Missing<wbr />Conditional<wbr />Parameter</code>

`FormMissingConditionalParameter` signifies an error when required parameter based on conditions is missing

filename: Status Code: 422
```json
{
  "shortMessage": "is missing",
  "longMessage": "`<param>` is required when `<leftCondition>` is `<rightCondition>`.",
  "code": "form_conditional_param_missing"
}
```

### <code><wbr />Form<wbr />Missing<wbr />Conditional<wbr />Parameter<wbr />On<wbr />Existence</code>

`FormMissingConditionalParameterOnExistence` signifies an error when parameter is required because of the existence of another

filename: Status Code: 422
```json
{
  "shortMessage": "is missing",
  "longMessage": "`<missingParam>` is required when `<conditionalParam>` is present.",
  "code": "form_conditional_param_missing",
  "meta": {
    "name": "missingparam"
  }
}
```

### <code><wbr />Form<wbr />Missing<wbr />Parameter</code>

`FormMissingParameter` signifies an error when an expected form parameter is missing

filename: Status Code: 422
```json
{
  "shortMessage": "is missing",
  "longMessage": "<param> must be included.",
  "code": "form_param_missing",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Missing<wbr />Resource</code>

`FormMissingResource` signifies an error when the form parameter is referring to a missing resource

filename: Status Code: 422
```json
{
  "shortMessage": "is missing",
  "longMessage": "The resource associated with the supplied <param> was not found.",
  "code": "form_resource_not_found",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Nil<wbr />Parameter</code>

`FormNilParameter` signifies an error when a nil parameter is found in a form

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_param_nil",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Not<wbr />Allowed<wbr />To<wbr />Disable<wbr />Default<wbr />Second<wbr />Factor</code>

`FormNotAllowedToDisableDefaultSecondFactor` signifies an error when trying to disable the default flag from a second-factor

filename: Status Code: 422
```json
{
  "shortMessage": "The default second factor method can only be changed by assigning another method as the default.",
  "longMessage": "The default second factor method can only be changed by assigning another method as the default.",
  "code": "form_disable_default_second_factor_not_allowed",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Array<wbr />Size<wbr />Exceeded</code>

`FormParameterArraySizeExceeded` signifies an error when the given array exceeds the maximum allowed size

filename: Status Code: 422
```json
{
  "shortMessage": "exceeds maximum size",
  "longMessage": "<parameter> should not exceed %d items.",
  "code": "form_param_array_size_exceeded",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Deprecated</code>

`FormParameterDeprecated` signifies an error when a form parameter has been
deprecated and is no longer accepted by the endpoint. The resolution argument
can describe the recommended replacement (e.g. a different endpoint) and is
appended to the long message when non-empty.

filename: Status Code: 422
```json
{
  "shortMessage": "is deprecated",
  "longMessage": "is deprecated",
  "code": "form_param_deprecated",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Max<wbr />Length<wbr />Exceeded</code>

`FormParameterMaxLengthExceeded` signifies an error when the given param value exceeds the maximum allowed length

filename: Status Code: 422
```json
{
  "shortMessage": "exceeds maximum length",
  "longMessage": "<parameter> should not exceed %d characters.",
  "code": "form_param_max_length_exceeded",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Min<wbr />Length<wbr />Exceeded</code>

`FormParameterMinLengthExceeded` signifies an error when the given param value is less than the minimum allowed length

filename: Status Code: 422
```json
{
  "shortMessage": "does not reach minimum length",
  "longMessage": "<parameter> must be at least %d characters long.",
  "code": "form_param_min_length_exceeded",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Not<wbr />Allowed<wbr />Conditionally</code>

`FormParameterNotAllowedConditionally` signifies an error when parameter is not allowed based on condition

filename: Status Code: 422
```json
{
  "shortMessage": "is not allowed",
  "longMessage": "`<param>` isn't allowed when `<leftCondition>` is <rightCondition>.",
  "code": "form_conditional_param_disallowed",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Not<wbr />Allowed<wbr />If<wbr />Another<wbr />Parameter<wbr />Is<wbr />Present</code>

`FormParameterNotAllowedIfAnotherParameterIsPresent` signifies an error when a parameter is present but
is not allowed because another parameter is also present

filename: Status Code: 422
```json
{
  "shortMessage": "is not allowed",
  "longMessage": "`<notAllowedParam>` isn't allowed when `<existingParam>` is present.",
  "code": "form_conditional_param_disallowed",
  "meta": {
    "name": "notallowedparam"
  }
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Size<wbr />Too<wbr />Large</code>

`FormParameterSizeTooLarge` signifies an error when a parameter exceeds the max allowed size

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_param_exceeds_allowed_size",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Parameter<wbr />Value<wbr />Too<wbr />Large</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Value too large",
  "longMessage": "The value of <param> can't be greater than %d",
  "code": "form_param_value_too_large",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Password<wbr />Digest<wbr />Invalid</code>

`FormPasswordDigestInvalid` signifies an error when the provided password\_digest is not valid for the provided password\_hasher

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_password_digest_invalid_code",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Password<wbr />Validation<wbr />Failed</code>

`FormPasswordValidationFailed` signifies a generic error when the password validation failed

filename: Status Code: 422
```json
{
  "shortMessage": "Incorrect password. Please try again.",
  "longMessage": "Incorrect password. Please try again.",
  "code": "form_password_validation_failed",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Public<wbr />Client<wbr />Requires<wbr />P<wbr />K<wbr />C<wbr />E</code>

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "PKCE is required for OAuth clients without a secret",
  "code": "form_public_client_requires_pkce",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Pwned<wbr />Password</code>

`FormPwnedPassword` signifies an error when the chosen password has been found in the pwned list

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_password_pwned",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Unknown<wbr />Parameter<wbr />Due<wbr />To<wbr />Disabled<wbr />Feature</code>

`FormUnknownParameterDueToDisabledFeature` signifies an error when an unexpected parameter is found in a form due to a disabled feature

filename: Status Code: 422
```json
{
  "shortMessage": "is unknown",
  "longMessage": "<param> is not a valid parameter for this request.<possibleResolution>",
  "code": "form_param_unknown",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Unverified<wbr />Identification</code>

`FormUnverifiedIdentification` signifies an error when the identification included in the form is unverified

filename: Status Code: 422
```json
{
  "shortMessage": "is unverified",
  "longMessage": "This identification needs to be verified before you can perform this action.",
  "code": "form_verification_needed",
  "meta": {
    "name": "param"
  }
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
  "shortMessage": "",
  "longMessage": "<parameter> cannot be a phone number. Please choose a different username.",
  "code": "form_username_cannot_be_phone_number",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Validation<wbr />Failed</code>

`FormValidationFailed` converts validator.ValidationErrors to Error.

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "<sanitizedField> is invalid",
  "code": "form_param_value_invalid",
  "meta": {
    "name": "sanitizedfield"
  }
}
```

## Fraud

### <code><wbr />Fraud<wbr />Action<wbr />Blocked</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Action blocked",
  "longMessage": "This action was detected as suspicious and has been blocked. If you believe this was a mistake, please contact support.",
  "code": "action_blocked"
}
```

## Home Url

### <code><wbr />Home<wbr />U<wbr />R<wbr />L<wbr />Taken</code>

`HomeURLTaken` signifies an error when the root domain of the provided home\_url already in use by another application

filename: Status Code: 422
```json
{
  "shortMessage": "Domain already in use",
  "longMessage": "The <homeURL> root domain is already in use by another application.",
  "code": "home_url_taken",
  "meta": {
    "name": "paramname"
  }
}
```

### <code><wbr />Home<wbr />U<wbr />R<wbr />L<wbr />Taken<wbr />By<wbr />Provider</code>

`HomeURLTakenByProvider` signifies an error when the root domain of the
provided home\_url is already used by a provider-managed app.

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "longMessage": "The <homeURL> root domain is already in use by a <providerName> app. Delete the <providerName> app or contact <providerName> support to remove the domain before using it in Clerk.",
  "code": "home_url_taken",
  "meta": {
    "name": "paramname"
  }
}
```

### <code><wbr />Known<wbr />Hosting<wbr />Domain</code>

`KnownHostingDomain` signifies an error when the domain extracted from the provided home\_url belongs to a
known hosting service and cannot be used to deploy production apps

filename: Status Code: 422
```json
{
  "shortMessage": "Known hosting domain",
  "longMessage": "The <domain> domain cannot be used to deploy production apps.",
  "code": "known_hosting_domain",
  "meta": {
    "name": "paramname"
  }
}
```

### <code><wbr />Reserved<wbr />Domain</code>

`ReservedDomain` signifies an error when the domain extracted from the provided home\_url is reserved by Clerk

filename: Status Code: 422
```json
{
  "shortMessage": "Domain reserved by Clerk",
  "longMessage": "The <domain> domain is reserved by Clerk.",
  "code": "reserved_domain",
  "meta": {
    "name": "paramname"
  }
}
```

### <code><wbr />Reserved<wbr />Subdomain</code>

`ReservedSubdomain` signifies an error when the subdomain extracted from the provided home\_url is reserved by Clerk

filename: Status Code: 422
```json
{
  "shortMessage": "Reserved subdomain",
  "longMessage": "The <subdomain> subdomain is reserved by Clerk.",
  "code": "reserved_subdomain",
  "meta": {
    "name": "paramname"
  }
}
```

## Identifications

### <code><wbr />Create<wbr />Second<wbr />Factor<wbr />Unverified</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Create failed",
  "longMessage": "Unverified identifications cannot be a second factor",
  "code": "identification_create_second_factor_unverified"
}
```

### <code><wbr />Identification<wbr />Not<wbr />Found</code>

`IdentificationNotFound` signifies an error when comm is not found

filename: Status Code: 404
```json
{
  "shortMessage": "Resource not found",
  "longMessage": "Resource not found",
  "code": "resource_not_found"
}
```

### <code><wbr />Last<wbr />Identification<wbr />Set<wbr />For2<wbr />F<wbr />A<wbr />Failed</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Update failed",
  "longMessage": "You cannot set your last identification as second factor.",
  "code": "identification_update_failed"
}
```

### <code><wbr />Update<wbr />Second<wbr />Factor<wbr />Unverified</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Update failed",
  "longMessage": "Cannot update second factor attributes for unverified identification",
  "code": "identification_update_second_factor_unverified"
}
```

## Images

### <code><wbr />Image<wbr />Decoding<wbr />Failed</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Image decode error",
  "longMessage": "The image could not be decoded. Please ensure the image is valid and try again.",
  "code": "request_body_invalid"
}
```

### <code><wbr />Image<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "Image not found",
  "longMessage": "Image not found",
  "code": "image_not_found"
}
```

### <code><wbr />Image<wbr />Too<wbr />Large</code>

`ImageTooLarge` signifies an error when the image being uploaded is too large to handle.

filename: Status Code: 413
```json
{
  "shortMessage": "Image too large",
  "longMessage": "The image being uploaded is more than 10MB. Please choose a smaller one.",
  "code": "image_too_large"
}
```

### <code><wbr />Image<wbr />Type<wbr />Not<wbr />Supported</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Unsupported image type",
  "longMessage": "'<imageType>' images are not currently supported. Please consult the API documentation for more information.",
  "code": "request_body_invalid"
}
```

### <code><wbr />Request<wbr />Without<wbr />Image</code>

`RequestWithoutImage` signifies an error when no image was present in the request.

filename: Status Code: 400
```json
{
  "shortMessage": "Image file missing",
  "longMessage": "There was no image file present in the request",
  "code": "form_param_missing"
}
```

## Impersonation

### <code><wbr />Impersonation<wbr />Limit<wbr />Exceeded</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Impersonation limit exceeded",
  "longMessage": "Your application has reached the impersonation limit for your plan (%d/%d). The limit will reset at the beginning of the next billing period.",
  "code": "impersonation_limit_exceeded",
  "meta": "{\"Limit\": limit, \"Used\": used}"
}
```

## Instance Keys

### <code><wbr />Instance<wbr />Key<wbr />Required</code>

`InstanceKeyRequired` signifies an error when no instance keys exist

filename: Status Code: 400
```json
{
  "shortMessage": "Key required",
  "longMessage": "Please generate at least one instance key",
  "code": "instance_key_required"
}
```

## Instance Settings

### <code><wbr />Disabled<wbr />Instance<wbr />Restriction</code>

filename: Status Code: 422
```json
{
  "shortMessage": "is not allowed",
  "longMessage": "`<param>` isn't allowed to be set for this instance",
  "code": "disabled_instance_restriction",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Invalid<wbr />Captcha<wbr />Widget<wbr />Type</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Invalid captcha widget type",
  "longMessage": "The captcha widget type '<widgetType>' is invalid. Allowed values: <allowedTypes>",
  "code": "invalid_captcha_widget_type"
}
```

### <code><wbr />Invalid<wbr />Captcha<wbr />Widget<wbr />Type<wbr />Transition</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Invalid captcha widget type transition",
  "longMessage": "The captcha widget type cannot be changed from '<from>' to '<to>'.",
  "code": "invalid_captcha_widget_type"
}
```

## Instances

### <code><wbr />Breaks<wbr />Instance<wbr />Invariant</code>

`BreaksInstanceInvariant`Code

filename: Status Code: 400
```json
{
  "shortMessage": "Breaks instance invariant",
  "longMessage": "%v - This invariant is determined by your user settings",
  "code": "breaks_instance_invariant"
}
```

### <code><wbr />Instance<wbr />Not<wbr />Found</code>

`InstanceNotFound` signifies an error when no instance with given instanceID was found

filename: Status Code: 404
```json
{
  "shortMessage": "Instance not found",
  "longMessage": "No instance was found with id <instanceID>",
  "code": "resource_not_found"
}
```

### <code><wbr />Production<wbr />Instance<wbr />Exists</code>

`ProductionInstanceExists` signifies an error when trying to create a production instance
when there is already one

filename: Status Code: 400
```json
{
  "shortMessage": "You can only have one production instance.",
  "longMessage": "You can only have one production instance.",
  "code": "production_instance_exists"
}
```

## Internal

### <code><wbr />Bad<wbr />Request</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Bad request",
  "longMessage": "Bad request",
  "code": "bad_request"
}
```

### <code><wbr />Bad<wbr />Request<wbr />With<wbr />Message</code>

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "code": "bad_request"
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
  "shortMessage": "Conflict",
  "longMessage": "Conflict",
  "code": "conflict"
}
```

### <code><wbr />Quota<wbr />Exceeded</code>

403 - quota exceeded

filename: Status Code: 403
```json
{
  "shortMessage": "Quota exceeded",
  "longMessage": "Quota exceeded, you have reached your limit.",
  "code": "quota_exceeded"
}
```

### <code><wbr />Resource<wbr />Busy</code>

409 - resource locked

filename: Status Code: 409
```json
{
  "shortMessage": "resource busy",
  "longMessage": "This resource is currently being modified by another request. Please try again.",
  "code": "resource_locked"
}
```

### <code><wbr />Unexpected</code>

`Unexpected` is used for all unexpected errors
It unwraps the error chain to check if an API error was wrapped,
and returns that instead of creating a 500 error

filename: Status Code: 500
```json
{
  "shortMessage": "Oops, an unexpected error occurred",
  "longMessage": "There was an internal error on our servers. We've been notified and are working on fixing it.",
  "code": "internal_clerk_error"
}
```

## Invitations

### <code><wbr />Duplicate<wbr />Invitations</code>

`DuplicateInvitations` denotes an error when there are already invitations
for the given email addresses

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "There are already pending invitations for the following email addresses: <emails>",
  "code": "duplicate_record",
  "meta": {
    "emailaddresses": "emailaddresses"
  }
}
```

### <code><wbr />Invitation<wbr />Already<wbr />Accepted</code>

`InvitationAlreadyAccepted` denotes an error when someone tries to use
an invitation which is already accepted.

filename: Status Code: 400
```json
{
  "shortMessage": "Invitation is already accepted, try signing in instead.",
  "longMessage": "Invitation is already accepted, try signing in instead.",
  "code": "invitation_already_accepted"
}
```

### <code><wbr />Invitation<wbr />Already<wbr />Revoked</code>

`InvitationAlreadyRevoked` denotes an error when someone tries to revoke
an invitation which is already revoked.

filename: Status Code: 400
```json
{
  "shortMessage": "Invitation is already revoked.",
  "longMessage": "Invitation is already revoked.",
  "code": "invitation_already_revoked"
}
```

### <code><wbr />Invitation<wbr />Not<wbr />Found</code>

`InvitationNotFound` denotes an error when there is no invitation with
the given id

filename: Status Code: 404
```json
{
  "shortMessage": "not found",
  "longMessage": "No invitation was found with id <invitationID>.",
  "code": "resource_not_found"
}
```

### <code><wbr />Invitations<wbr />Not<wbr />Supported<wbr />In<wbr />Instance</code>

`InvitationsNotSupportedInInstance` denotes an error when user is
trying to create an invitation on an instance that doesn't support it

filename: Status Code: 400
```json
{
  "shortMessage": "Invitations are only supported on instances that accept email addresses.",
  "longMessage": "Invitations are only supported on instances that accept email addresses.",
  "code": "invitations_not_supported"
}
```

### <code><wbr />Revoked<wbr />Invitation</code>

`RevokedInvitation` denotes an error when the given invitation token
does not correspond to any invitations, which means that the invitation
has been removed.

filename: Status Code: 400
```json
{
  "shortMessage": "The invitation was revoked.",
  "longMessage": "The invitation was revoked.",
  "code": "revoked_invitation"
}
```

## Jwt Templates

### <code><wbr />J<wbr />W<wbr />T<wbr />Template<wbr />Not<wbr />Found</code>

`JWTTemplateNotFound` signifies an error when a JWT template was not found by the provided attribute

filename: Status Code: 404
```json
{
  "shortMessage": "JWT template not found",
  "longMessage": "No JWT template exists with <attribute>: <val>",
  "code": "resource_not_found"
}
```

### <code><wbr />J<wbr />W<wbr />T<wbr />Template<wbr />Reserved<wbr />Claim</code>

`JWTTemplateReservedClaim` denotes an error when the provided template contains a reserved claim.

filename: Status Code: 400
```json
{
  "shortMessage": "reserved claim used",
  "longMessage": "You can't use the reserved claim: '<claim>'",
  "code": "jwt_template_reserved_claim",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Session<wbr />Token<wbr />Template<wbr />Not<wbr />Deletable</code>

filename: Status Code: 403
```json
{
  "shortMessage": "session token template cannot be deleted",
  "longMessage": "This template cannot be deleted because it's a session token template",
  "code": "session_token_jwt_template"
}
```

## Machine Token

### <code><wbr />Machine<wbr />Token<wbr />Reserved<wbr />Claim</code>

`MachineTokenReservedClaim` denotes an error when the provided machine token claims object contains a reserved claim.

filename: Status Code: 400
```json
{
  "shortMessage": "reserved claim used",
  "longMessage": "You can't use the reserved claim: '<claim>'",
  "code": "machine_token_reserved_claim",
  "meta": {
    "name": "param"
  }
}
```

## Management

### <code><wbr />Duplicate<wbr />List<wbr />Items<wbr />Not<wbr />Allowed</code>

filename: Status Code: 422
```json
{
  "shortMessage": "duplicate list items not allowed",
  "longMessage": "duplicate list items not allowed: <param>",
  "code": "duplicate_list_items_not_allowed"
}
```

### <code><wbr />Invalid<wbr />Environment<wbr />Type</code>

filename: Status Code: 400
```json
{
  "shortMessage": "invalid environment type",
  "longMessage": "invalid environment types: <envTypes>",
  "code": "invalid_environment_type"
}
```

### <code><wbr />Too<wbr />Many<wbr />Secret<wbr />Keys</code>

filename: Status Code: 400
```json
{
  "shortMessage": "too many secret keys",
  "longMessage": "You can only rotate secret keys when your instance has exactly one key.",
  "code": "too_many_secret_keys"
}
```

## Network

### <code><wbr />Gateway<wbr />Timeout</code>

`GatewayTimeout` signifies an error when a 3rd party service takes too long to respond.

filename: Status Code: 504
```json
{
  "shortMessage": "Gateway Timeout",
  "longMessage": "A request to a 3rd party service timed out",
  "code": "gateway_timeout"
}
```

## Oauth

### <code><wbr />Custom<wbr />O<wbr />Auth<wbr />Provider<wbr />Cannot<wbr />Delete<wbr />Active</code>

filename: Status Code: 400
```json
{
  "shortMessage": "active custom OAuth provider cannot be deleted",
  "longMessage": "The custom OAuth provider %q is currently active and cannot be deleted. You can disable it instead.",
  "code": "custom_oauth_provider_cannot_delete_active"
}
```

### <code><wbr />Custom<wbr />O<wbr />Auth<wbr />Provider<wbr />Cannot<wbr />Use<wbr />Discovery<wbr />U<wbr />R<wbr />L</code>

filename: Status Code: 422
```json
{
  "shortMessage": "custom OAuth provider cannot use discovery URL",
  "longMessage": "The custom OAuth provider cannot use the discovery URL. Please provide the necessary configuration manually.",
  "code": "custom_oauth_provider_cannot_use_discovery_url",
  "meta": {
    "name": "discovery_url"
  }
}
```

### <code><wbr />Custom<wbr />O<wbr />Auth<wbr />Provider<wbr />Discovery<wbr />Issuer<wbr />Mismatch</code>

filename: Status Code: 422
```json
{
  "shortMessage": "issuer mismatch in custom OAuth provider discovery URL",
  "longMessage": "The issuer in the discovery URL (<url>) does not match the issuer returned in the configuration (<issuer>).",
  "code": "custom_oauth_provider_discovery_issuer_mismatch",
  "meta": {
    "name": "discovery_url"
  }
}
```

### <code><wbr />Custom<wbr />Oauth<wbr />Provider<wbr />Discovery<wbr />Server<wbr />Retrieval<wbr />Error</code>

filename: Status Code: 422
```json
{
  "shortMessage": "error retrieving OAuth response from provider's discovery URL",
  "longMessage": "An error was encountered when attempting to retrieve metadata from the oauth url %q: %q",
  "code": "custom_oauth_provider_discovery_server_retrieval_error",
  "meta": {
    "name": "discovery_url"
  }
}
```

### <code><wbr />O<wbr />Auth<wbr />Missing<wbr />Access<wbr />Token</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Missing OAuth access token",
  "longMessage": "OAuth access token is missing",
  "code": "oauth_missing_access_token"
}
```

### <code><wbr />O<wbr />Auth<wbr />Missing<wbr />Refresh<wbr />Token</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Cannot refresh OAuth access token",
  "longMessage": "The current access token has expired and we cannot refresh it, because the authorization server hasn't provided us with a refresh token",
  "code": "oauth_missing_refresh_token"
}
```

### <code><wbr />O<wbr />Auth<wbr />Token<wbr />Provider<wbr />Not<wbr />Enabled</code>

filename: Status Code: 404
```json
{
  "shortMessage": "OAuth provider not enabled",
  "longMessage": "Single-sign on for this OAuth provider is not enabled in the instance settings.",
  "code": "oauth_token_provider_not_enabled"
}
```

### <code><wbr />O<wbr />Auth<wbr />Token<wbr />Retrieval<wbr />Error</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Token retrieval failed",
  "longMessage": "Failed to retrieve a new access token from the OAuth provider",
  "code": "oauth_token_retrieval_error"
}
```

### <code><wbr />Unsupported<wbr />Oauth<wbr />Provider</code>

`UnsupportedOauthProvider` signifies an error when an instance tries to enable
an OAuth external provider which is not supported.

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "%v OAuth is not supported. Please contact us if you think this error should not appear.",
  "code": "oauth_unsupported_provider"
}
```

## Oauth Application

### <code><wbr />Duplicate<wbr />O<wbr />Auth<wbr />Redirect<wbr />U<wbr />R<wbr />I</code>

filename: Status Code: 400
```json
{
  "shortMessage": "duplicate redirect URI",
  "longMessage": "the redirect URI already exists",
  "code": "duplicate_record"
}
```

### <code><wbr />O<wbr />Auth<wbr />Application<wbr />Consent<wbr />Screen<wbr />Cannot<wbr />Be<wbr />Disabled</code>

filename: Status Code: 422
```json
{
  "shortMessage": "consent screen cannot be disabled",
  "longMessage": "Consent screen cannot be disabled for a dynamically registered OAuth Application",
  "code": "oauth_application_consent_screen_cannot_be_disabled"
}
```

## Organizations

### <code><wbr />Already<wbr />A<wbr />Member<wbr />Of<wbr />Organization</code>

400 - User with given identifier is already a member of the
organization and cannot be added again

filename: Status Code: 400
```json
{
  "shortMessage": "already a member",
  "longMessage": "<user> is already a member of the organization.",
  "code": "already_a_member_in_organization"
}
```

### <code><wbr />Force<wbr />Organization<wbr />Selection<wbr />Not<wbr />Allowed<wbr />When<wbr />Organizations<wbr />Disabled</code>

filename: Status Code: 422
```json
{
  "shortMessage": "not allowed",
  "longMessage": "`force_organization_selection` cannot be enabled when organizations are disabled. Please enable organizations first.",
  "code": "force_organization_selection_not_allowed_when_organizations_disabled"
}
```

### <code><wbr />Missing<wbr />Organization<wbr />Permission</code>

filename: Status Code: 403
```json
{
  "shortMessage": "missing permission",
  "longMessage": "Current user is missing an organization permission.",
  "code": "missing_organization_permission",
  "meta": {
    "permissions": "permissions"
  }
}
```

### <code><wbr />Not<wbr />A<wbr />Member<wbr />In<wbr />Organization</code>

403 - Only for organization members
Deprecated: This error reveals the existence of an organization to an unauthorized user.
Use OrganizationNotFoundOrUnauthorized instead, and ensure other pathways that error
when the organization isn't found also use OrganizationNotFoundOrUnauthorized

filename: Status Code: 403
```json
{
  "shortMessage": "not a member",
  "longMessage": "Current user is not a member of the organization. Only organization members can perform this action.",
  "code": "not_a_member_in_organization"
}
```

### <code><wbr />Organization<wbr />Already<wbr />Has<wbr />S<wbr />S<wbr />O<wbr />Connection</code>

filename: Status Code: 422
```json
{
  "shortMessage": "this organization already has an SSO connection",
  "longMessage": "This organization already has an SSO connection.",
  "code": "organization_already_has_sso_connection",
  "meta": {
    "name": "organization_id"
  }
}
```

### <code><wbr />Organization<wbr />Creator<wbr />Not<wbr />Found</code>

400 - Creator doesn't exist

filename: Status Code: 400
```json
{
  "shortMessage": "creator not found",
  "longMessage": "No users found with id <userID>.",
  "code": "organization_creator_not_found"
}
```

### <code><wbr />Organization<wbr />Domain<wbr />Already<wbr />Exists</code>

filename: Status Code: 422
```json
{
  "shortMessage": "organizaton domain already exists",
  "longMessage": "This domain is already used by another organization.",
  "code": "organization_domain_already_exists",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Organization<wbr />Domain<wbr />Blocked</code>

filename: Status Code: 422
```json
{
  "shortMessage": "blocked email domain",
  "longMessage": "This is a blocked email provider domain. Please use a different one.",
  "code": "organization_domain_blocked",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Organization<wbr />Domain<wbr />Common</code>

filename: Status Code: 422
```json
{
  "shortMessage": "common email domain",
  "longMessage": "This is a common email provider domain. Please use a different one.",
  "code": "organization_domain_common",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Organization<wbr />Domain<wbr />Enrollment<wbr />Mode<wbr />Not<wbr />Enabled</code>

filename: Status Code: 403
```json
{
  "shortMessage": "organization enrollment mode not enabled",
  "longMessage": "Enrollment mode <enrollmentMode> is not enabled for this instances's organizations.",
  "code": "organization_domain_enrollment_mode_not_enabled"
}
```

### <code><wbr />Organization<wbr />Domain<wbr />Quota<wbr />Exceeded</code>

filename: Status Code: 403
```json
{
  "shortMessage": "organization domains quota exceeded",
  "longMessage": "You have reached your limit of %d domains per organization.",
  "code": "organization_domain_quota_exceeded"
}
```

### <code><wbr />Organization<wbr />Instance<wbr />Roles<wbr />Quota<wbr />Exceeded</code>

filename: Status Code: 403
```json
{
  "shortMessage": "organization roles for instance quota exceeded",
  "longMessage": "You have reached your limit of %d organization roles per instance.",
  "code": "organization_instance_roles_quota_exceeded"
}
```

### <code><wbr />Organization<wbr />Invitation<wbr />Not<wbr />Unique</code>

filename: Status Code: 400
```json
{
  "shortMessage": "organization invitation not unique",
  "longMessage": "Organizations cannot have duplicate pending invitations for an email address.",
  "code": "organization_invitation_not_unique"
}
```

### <code><wbr />Organization<wbr />Membership<wbr />Quota<wbr />Exceeded</code>

filename: Status Code: 403
```json
{
  "shortMessage": "organization membership quota exceeded",
  "longMessage": "You have reached your limit of %d organization memberships, including outstanding invitations.",
  "code": "organization_membership_quota_exceeded"
}
```

### <code><wbr />Organization<wbr />Membership<wbr />S<wbr />C<wbr />I<wbr />M<wbr />Managed</code>

filename: Status Code: 409
```json
{
  "shortMessage": "membership role managed by SCIM",
  "longMessage": "This membership is managed by a SCIM directory and cannot be changed manually.",
  "code": "organization_membership_managed_by_scim"
}
```

### <code><wbr />Organization<wbr />Minimum<wbr />Permissions<wbr />Needed</code>

filename: Status Code: 400
```json
{
  "shortMessage": "minimum organization permissions needed",
  "longMessage": "There has to be at least one organization member with the minimum required permissions",
  "code": "organization_minimum_permissions_needed"
}
```

### <code><wbr />Organization<wbr />Missing<wbr />Creator<wbr />Role<wbr />Permissions</code>

filename: Status Code: 422
```json
{
  "shortMessage": "missing permissions for creator role",
  "longMessage": "The creator role must contain the following permissions: <permissionKeys>",
  "code": "organization_missing_creator_role_permissions"
}
```

### <code><wbr />Organization<wbr />Name<wbr />Invalid</code>

filename: Status Code: 422
```json
{
  "shortMessage": "invalid organization name",
  "longMessage": "The organization name %q is invalid: <name>",
  "code": "form_param_value_invalid",
  "meta": {
    "name": "name"
  }
}
```

### <code><wbr />Organization<wbr />Not<wbr />Enabled<wbr />In<wbr />Instance</code>

filename: Status Code: 403
```json
{
  "shortMessage": "access denied",
  "longMessage": "The organizations feature is not enabled for this instance. You can enable it at https://dashboard.clerk.com.",
  "code": "organization_not_enabled_in_instance"
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
  "shortMessage": "not found",
  "longMessage": "Given organization not found.",
  "code": "resource_not_found"
}
```

### <code><wbr />Organization<wbr />Not<wbr />Found<wbr />Or<wbr />Unauthorized</code>

404 - Used for any case

filename: Status Code: 404
```json
{
  "shortMessage": "not found or unauthorized",
  "longMessage": "Given organization not found, or you don't have permission to access the organization",
  "code": "organization_not_found_or_unauthorized"
}
```

### <code><wbr />Organization<wbr />Permission<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "not found",
  "longMessage": "Organization permission not found",
  "code": "resource_not_found"
}
```

### <code><wbr />Organization<wbr />Role<wbr />Assigned<wbr />To<wbr />Members</code>

filename: Status Code: 422
```json
{
  "shortMessage": "role is assigned to organization members",
  "longMessage": "The organization role is currently assigned to one or more organization members.",
  "code": "organization_role_assigned_members"
}
```

### <code><wbr />Organization<wbr />Role<wbr />Exists<wbr />In<wbr />Invitations</code>

filename: Status Code: 422
```json
{
  "shortMessage": "role exists in pending organization invitations",
  "longMessage": "The organization role exists in one or more pending organization invitations. Please revoke these invitations to proceed.",
  "code": "organization_role_exists_in_invitations"
}
```

### <code><wbr />Organization<wbr />Role<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "not found",
  "longMessage": "Organization role not found",
  "code": "resource_not_found",
  "meta": {
    "name": "paramname"
  }
}
```

### <code><wbr />Organization<wbr />Role<wbr />Permission<wbr />Association<wbr />Exists</code>

filename: Status Code: 409
```json
{
  "shortMessage": "permission already assigned to role",
  "longMessage": "This organization permission is already associated to this organization role.",
  "code": "organization_role_permission_association_exists"
}
```

### <code><wbr />Organization<wbr />Role<wbr />Used<wbr />As<wbr />Creator<wbr />Role</code>

filename: Status Code: 422
```json
{
  "shortMessage": "role is used as the creator role",
  "longMessage": "The organization role cannot be deleted as it is currently used as the creator role.",
  "code": "organization_role_default_creator_role"
}
```

### <code><wbr />Organization<wbr />Role<wbr />Used<wbr />As<wbr />Domain<wbr />Default<wbr />Role</code>

filename: Status Code: 422
```json
{
  "shortMessage": "role is used as the domain default role",
  "longMessage": "The organization role cannot be deleted as it is currently used as the default domain role.",
  "code": "organization_role_domain_default_role"
}
```

### <code><wbr />Organizations<wbr />Disable<wbr />Not<wbr />Allowed</code>

filename: Status Code: 400
```json
{
  "shortMessage": "cannot disable organizations",
  "longMessage": "Cannot disable organizations because <reason>.",
  "code": "organizations_disable_not_allowed"
}
```

### <code><wbr />Organization<wbr />System<wbr />Permission<wbr />Not<wbr />Modifiable</code>

filename: Status Code: 403
```json
{
  "shortMessage": "organization system permission cannot be modified",
  "longMessage": "This organization permission cannot be modified because it is a system permission.",
  "code": "organization_system_permission_not_modifiable"
}
```

## Platform

### <code><wbr />Platform<wbr />A<wbr />P<wbr />I<wbr />Policy<wbr />Violation</code>

`PlatformAPIPolicyViolation` signifies policy or issuer restrictions on OAuth access tokens for the Platform API (HTTP 403).

filename: Status Code: 403
```json
{
  "shortMessage": "Authentication policy violation",
  "longMessage": "This request cannot be completed due to a policy restriction.",
  "code": "authorization_invalid"
}
```

### <code><wbr />Platform<wbr />A<wbr />P<wbr />I<wbr />Request<wbr />Not<wbr />Allowed</code>

`PlatformAPIRequestNotAllowed` signifies that the Platform API request is forbidden for the authenticated principal or target resource (HTTP 403).

filename: Status Code: 403
```json
{
  "shortMessage": "Request not allowed",
  "longMessage": "This Platform API request cannot be completed for the authenticated principal or resource.",
  "code": "authorization_invalid"
}
```

### <code><wbr />Platform<wbr />A<wbr />P<wbr />I<wbr />Unrecognized<wbr />Credential</code>

`PlatformAPIUnrecognizedCredential` signifies that the bearer credential does not match any supported Platform API authentication format.

filename: Status Code: 401
```json
{
  "shortMessage": "Unrecognized credential",
  "longMessage": "The credential format is not recognized for the Platform API.",
  "code": "platform_api_unrecognized_credential"
}
```

### <code><wbr />Platform<wbr />O<wbr />Auth<wbr />Access<wbr />Token<wbr />Invalid</code>

`PlatformOAuthAccessTokenInvalid` signifies that an OAuth access token could not be parsed or verified.

filename: Status Code: 401
```json
{
  "shortMessage": "Invalid OAuth access token",
  "longMessage": "The OAuth access token is invalid, malformed, or could not be verified.",
  "code": "platform_oauth_access_token_invalid"
}
```

### <code><wbr />Platform<wbr />O<wbr />Auth<wbr />Access<wbr />Token<wbr />Missing<wbr />Claims</code>

`PlatformOAuthAccessTokenMissingClaims` signifies that a JWT access token is missing required claims.

filename: Status Code: 401
```json
{
  "shortMessage": "Invalid OAuth access token",
  "longMessage": "Invalid OAuth access token",
  "code": "platform_oauth_access_token_missing_claims",
  "meta": {
    "claims": "cp"
  }
}
```

## Pricing

### <code><wbr />Unsupported<wbr />Subscription<wbr />Plan<wbr />Features</code>

filename: Status Code: 402
```json
{
  "shortMessage": "Unsupported plan features",
  "longMessage": "Some features are not supported in your current plan. Upgrade your subscription to unlock them.",
  "code": "unsupported_subscription_plan_features",
  "meta": {
    "unsupportedfeatures": "unsupportedfeatures"
  }
}
```

## Public Keys

### <code><wbr />Public<wbr />Key<wbr />Not<wbr />Found</code>

`PublicKeyNotFound` signifies an error when no public key was found with the given id

filename: Status Code: 404
```json
{
  "shortMessage": "Public key not found",
  "longMessage": "No public key was found with id <publicKeyID>",
  "code": "resource_not_found"
}
```

## Redirect Urls

### <code><wbr />Redirect<wbr />U<wbr />R<wbr />L<wbr />Not<wbr />Found</code>

`RedirectURLNotFound` signifies an error when a RedirectURL was not found by the provided attribute

filename: Status Code: 404
```json
{
  "shortMessage": "Redirect url not found",
  "longMessage": "No RedirectURL exists with <attribute>: <val>",
  "code": "resource_not_found"
}
```

## Requests

### <code><wbr />Bulk<wbr />Size<wbr />Exceeded</code>

filename: Status Code: 400
```json
{
  "shortMessage": "bulk size exceeded",
  "longMessage": "Parameters exceed the maximum allowed bulk processing size of %d.",
  "code": "bulk_size_exceeded"
}
```

### <code><wbr />Failed<wbr />To<wbr />Parse<wbr />Request<wbr />Body</code>

`FailedToParseRequestBody` is a dynamic error which should be used after
receiving an error from a JSON decode attempt.

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "%v is invalid. Received %v, must be of type %v.",
  "code": "form_param_value_invalid"
}
```

### <code><wbr />Invalid<wbr />Request<wbr />Body</code>

`InvalidRequestBody` signifies an error when the body of the request does not conform to the expected format

filename: Status Code: 400
```json
{
  "shortMessage": "Request body invalid",
  "longMessage": "The request body is invalid. Please consult the API documentation for more information.",
  "code": "request_body_invalid"
}
```

### <code><wbr />Malformed<wbr />Publishable<wbr />Key</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Malformed publishable key",
  "longMessage": "Ensure the provided publishable key (<key>) is the one displayed in Dashboard",
  "code": "malformed_publishable_key"
}
```

### <code><wbr />Malformed<wbr />Request<wbr />Parameters</code>

`MalformedRequestParameters` signifies an error when the request parameters are malformed and result in parsing errors

filename: Status Code: 400
```json
{
  "shortMessage": "Malformed request parameters",
  "longMessage": "The request parameters are malformed and could not be parsed",
  "code": "malformed_request_parameters"
}
```

### <code><wbr />Missing<wbr />One<wbr />Of<wbr />Query<wbr />Parameters</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Missing query parameter",
  "longMessage": "Either of the following query parameters must be provided: <parameters>.",
  "code": "missing_query_parameter"
}
```

### <code><wbr />Missing<wbr />Query<wbr />Parameter</code>

`MissingQueryParameter` denotes that the required query parameter, param, was
not provided by the request.

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "The query parameter '<param>' is missing from the request. Please consult the API documentation for more information.",
  "code": "missing_query_parameter"
}
```

### <code><wbr />Request<wbr />Body<wbr />Too<wbr />Large</code>

filename: Status Code: 413
```json
{
  "shortMessage": "Request body too large",
  "longMessage": "The request body exceeds the maximum allowed size of %d bytes.",
  "code": "request_body_too_large"
}
```

### <code><wbr />Unsupported<wbr />Content<wbr />Type</code>

`UnsupportedContentType` signifies an error when provided content type is unsupported

filename: Status Code: 415
```json
{
  "shortMessage": "Content-Type is unsupported",
  "longMessage": "Content-Type <actual> is unsupported. You should use <expected> instead.",
  "code": "unsupported_content_type"
}
```

## Saml

### <code><wbr />S<wbr />A<wbr />M<wbr />L<wbr />Connection<wbr />Cant<wbr />Be<wbr />Activated</code>

filename: Status Code: 422
```json
{
  "shortMessage": "SAML Connection can't be activated",
  "longMessage": "You have to provide the <fields> before you are able to activate this connection.",
  "code": "saml_connection_cant_be_activated"
}
```

### <code><wbr />S<wbr />A<wbr />M<wbr />L<wbr />Failed<wbr />To<wbr />Fetch<wbr />I<wbr />D<wbr />P<wbr />Metadata</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Failed to fetch IdP metadata",
  "longMessage": "We failed to fetch the IdP metadata. If the error persists, please provide the IdP configuration data explicitly.",
  "code": "saml_failed_to_fetch_idp_metadata"
}
```

### <code><wbr />S<wbr />A<wbr />M<wbr />L<wbr />Failed<wbr />To<wbr />Parse<wbr />I<wbr />D<wbr />P<wbr />Metadata</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Failed to parse IdP metadata",
  "longMessage": "We failed to parse the IdP metadata. If the error persists, please provide the IdP configuration data explicitly.",
  "code": "saml_failed_to_parse_idp_metadata"
}
```

### <code><wbr />S<wbr />A<wbr />M<wbr />L<wbr />Metadata<wbr />Missing<wbr />Fields</code>

filename: Status Code: 422
```json
{
  "shortMessage": "IdP metadata is missing required fields",
  "longMessage": "The IdP metadata is missing the following required fields: <fields>",
  "code": "saml_metadata_missing_fields",
  "meta": {
    "missingfields": "missingfields"
  }
}
```

## Scim

### <code><wbr />S<wbr />C<wbr />I<wbr />M<wbr />Attribute<wbr />Managed<wbr />By<wbr />Directory</code>

`SCIMAttributeManagedByDirectory` returns a 409 Conflict error when attempting to
update an attribute that is managed by a SCIM directory.

filename: Status Code: 409
```json
{
  "shortMessage": "attribute managed by SCIM",
  "longMessage": "attribute managed by SCIM",
  "code": "attribute_managed_by_scim",
  "meta": {
    "name": "paramname"
  }
}
```

### <code><wbr />S<wbr />C<wbr />I<wbr />M<wbr />Group<wbr />Role<wbr />Mapping<wbr />Disabled</code>

`SCIMGroupRoleMappingDisabled` returns an error when attempting to mutate group role
mappings on a SCIM directory that has role mapping disabled.

filename: Status Code: 400
```json
{
  "shortMessage": "role mapping disabled",
  "longMessage": "Role mapping is disabled for this SCIM directory. Enable role mapping to add, edit, or remove mappings.",
  "code": "feature_not_enabled"
}
```

## Session Refresh

### <code><wbr />Session<wbr />Refresh<wbr />Consumed<wbr />Expired<wbr />Session<wbr />Token</code>

filename: Status Code: 401
```json
{
  "shortMessage": "expired session token consumed",
  "longMessage": "The provided expired session token was already consumed in a previous refresh request",
  "code": "session_refresh_expired_session_token_consumed"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />Expired<wbr />Session<wbr />Token<wbr />Invalid</code>

filename: Status Code: 401
```json
{
  "shortMessage": "Invalid expired_token param",
  "longMessage": "The session token provided could not be successfully verified",
  "code": "expired_session_token_invalid"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />Expired<wbr />Session<wbr />Token<wbr />Too<wbr />Old</code>

filename: Status Code: 401
```json
{
  "shortMessage": "session token too old",
  "longMessage": "The provided expired session token is too old",
  "code": "session_refresh_expired_session_token_too_old"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />Inactive<wbr />Session</code>

filename: Status Code: 401
```json
{
  "shortMessage": "session inactive",
  "longMessage": "The provided session is not active",
  "code": "session_refresh_inactive_session"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />Ineligible<wbr />Token</code>

filename: Status Code: 401
```json
{
  "shortMessage": "expired session token ineligible",
  "longMessage": "The provided expired session token is not eligible for refresh",
  "code": "session_refresh_session_token_ineligible"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />Invalid<wbr />Request<wbr />Origin</code>

filename: Status Code: 401
```json
{
  "shortMessage": "Request origin is invalid",
  "longMessage": "The request_origin parameter could not be parsed",
  "code": "refresh_request_origin_invalid"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />Missing<wbr />A<wbr />Z<wbr />P</code>

filename: Status Code: 401
```json
{
  "shortMessage": "missing 'azp' claim",
  "longMessage": "No 'azp' claim present in the provided expired session token",
  "code": "expired_session_token_missing_azp"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />Missing<wbr />I<wbr />A<wbr />T</code>

filename: Status Code: 401
```json
{
  "shortMessage": "missing 'iat' claim",
  "longMessage": "No 'iat' claim present in the provided expired session token",
  "code": "session_refresh_expired_session_token_missing_iat"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />Missing<wbr />S<wbr />I<wbr />D</code>

filename: Status Code: 401
```json
{
  "shortMessage": "missing 'sid' claim",
  "longMessage": "No 'sid' claim present in the provided expired session token",
  "code": "expired_session_token_missing_sid"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />Not<wbr />Enabled</code>

filename: Status Code: 401
```json
{
  "shortMessage": "not enabled",
  "longMessage": "This feature is not enabled in your instance",
  "code": "feature_not_enabled"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />Request<wbr />Origin<wbr />A<wbr />Z<wbr />P<wbr />Mismatch</code>

filename: Status Code: 401
```json
{
  "shortMessage": "Request origin does not match azp claim",
  "longMessage": "The request_origin parameter does not match the 'azp' claim of expired_token",
  "code": "refresh_request_origin_azp_mismatch"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />Session<wbr />Not<wbr />Found</code>

filename: Status Code: 401
```json
{
  "shortMessage": "Session not found",
  "longMessage": "No session was found with id <sessionID>",
  "code": "session_refresh_session_not_found"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />S<wbr />I<wbr />D<wbr />Mismatch</code>

filename: Status Code: 401
```json
{
  "shortMessage": "Session ID does not match the 'sid' claim",
  "longMessage": "The 'sid' claim of the provided expired session token does not match the session ID provided in the request path",
  "code": "refresh_sid_mismatch"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />Token<wbr />Not<wbr />Found</code>

filename: Status Code: 401
```json
{
  "shortMessage": "Refresh token not found",
  "longMessage": "The provided refresh token was not found",
  "code": "refresh_token_not_found"
}
```

### <code><wbr />Session<wbr />Refresh<wbr />User<wbr />Not<wbr />Found</code>

filename: Status Code: 401
```json
{
  "shortMessage": "user not found",
  "longMessage": "The provided user was not found",
  "code": "session_refresh_user_not_found"
}
```

## Sessions

### <code><wbr />Deprovisioned</code>

filename: Status Code: 401
```json
{
  "shortMessage": "account deprovisioned",
  "longMessage": "Your account is deprovisioned",
  "code": "deprovisioned"
}
```

### <code><wbr />Deprovisioned<wbr />Bad<wbr />Request</code>

filename: Status Code: 400
```json
{
  "shortMessage": "account deprovisioned",
  "longMessage": "The target user's account has been deprovisioned according to their external identity provider",
  "code": "deprovisioned"
}
```

### <code><wbr />Invalid<wbr />Session<wbr />Token</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid session token",
  "longMessage": "The token provided could not be successfully verified",
  "code": "invalid_session_token"
}
```

### <code><wbr />Session<wbr />Not<wbr />Found</code>

`SessionNotFound` signifies an error when no session with given sessionID was found

filename: Status Code: 404
```json
{
  "shortMessage": "Session not found",
  "longMessage": "No session was found with id <sessionID>",
  "code": "resource_not_found"
}
```

## Sign In

### <code><wbr />Identification<wbr />Claimed</code>

`IdentificationClaimed` signifies an error when the requested identification is already claimed by another user

filename: Status Code: 400
```json
{
  "shortMessage": "Identification claimed by another user",
  "longMessage": "One or more identifiers on this sign up have since been connected to a different User. Please sign up again.",
  "code": "identification_claimed"
}
```

## Sign In Tokens

### <code><wbr />Sign<wbr />In<wbr />Token<wbr />Cannot<wbr />Be<wbr />Revoked</code>

filename: Status Code: 400
```json
{
  "shortMessage": "cannot revoke",
  "longMessage": "Sign in token cannot be revoked because its status is <status>. Only pending tokens can be revoked.",
  "code": "sign_in_token_cannot_be_revoked_code"
}
```

## Sign Up

### <code><wbr />Invalid<wbr />Value<wbr />For<wbr />Sign<wbr />Up<wbr />Mode</code>

filename: Status Code: 422
```json
{
  "shortMessage": "is not allowed",
  "longMessage": "`<param>` isn't allowed to be `%v` when sign-up mode is set to <value>",
  "code": "sign_up_mode_restricted_invalid_value",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Sign<wbr />Up<wbr />Cannot<wbr />Be<wbr />Updated</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Sign up cannot be updated",
  "longMessage": "This sign up has reached a terminal state and cannot be updated",
  "code": "sign_up_cannot_be_updated"
}
```

### <code><wbr />Sign<wbr />Up<wbr />Mode<wbr />Invalid</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Invalid sign-up mode",
  "longMessage": "The sign-up mode '<mode>' is invalid. Allowed values: <allowedModes>",
  "code": "sign_up_mode_invalid"
}
```

## Signing Keys

### <code><wbr />Signing<wbr />Key<wbr />Not<wbr />Found</code>

`SigningKeyNotFound` signifies an error when no signing key with a given signingKeyID was found

filename: Status Code: 404
```json
{
  "shortMessage": "Signing key not found",
  "longMessage": "No signing key was found with id <signingKeyID>",
  "code": "resource_not_found"
}
```

## Sms

### <code><wbr />S<wbr />M<wbr />S<wbr />Country<wbr />Removal<wbr />Restricted</code>

`SMSCountryRemovalRestricted` signals that the caller tried to remove one or more
tier B-F countries from the SMS blocklist on an instance whose plan lacks the
phone\_code feature. Removing those countries is restricted to prevent SMS pumping abuse on
free/dev instances; activating them requires upgrading the plan or contacting support.

filename: Status Code: 422
```json
{
  "shortMessage": "SMS country removal restricted",
  "longMessage": "Cannot remove the following countries from the SMS blocklist without an upgraded plan: %v. Contact support to activate these countries.",
  "code": "sms_country_removal_restricted",
  "meta": "{\"CountryCodes\": countryCodes}"
}
```

## Subscription Plans

### <code><wbr />Product<wbr />Not<wbr />Supported<wbr />By<wbr />Subscription<wbr />Plan</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Product not supported by subscription plan",
  "longMessage": "The product <productID> is not compatible with the current subscription plan",
  "code": "product_not_supported_by_subscription_plan"
}
```

## Templates

### <code><wbr />Invalid<wbr />Template<wbr />Body</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Invalid template body",
  "longMessage": "This template body is invalid and cannot be rendered successfully, please check for syntax errors",
  "code": "invalid_template_body",
  "meta": {
    "name": "body"
  }
}
```

### <code><wbr />Required<wbr />Variable<wbr />Missing</code>

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "longMessage": "Body should contain the {{<requiredVariable>}} variable",
  "code": "required_variable_missing",
  "meta": {
    "name": "body"
  }
}
```

### <code><wbr />Template<wbr />Body<wbr />Modification<wbr />Not<wbr />Allowed</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Template body cannot be modified",
  "longMessage": "The body of template with slug <slug> can't be modified",
  "code": "template_body_modification_restricted"
}
```

### <code><wbr />Template<wbr />Deletion<wbr />Restricted</code>

`TemplateDeletionRestricted` signifies an error when a deletion is attempted for a built-in (non-custom) template

filename: Status Code: 400
```json
{
  "shortMessage": "Template deletion restricted",
  "longMessage": "Template with slug <slug> can't be deleted",
  "code": "template_deletion_restricted"
}
```

### <code><wbr />Template<wbr />Not<wbr />Found</code>

`TemplateNotFound` signifies an error when no template with given slug was found

filename: Status Code: 404
```json
{
  "shortMessage": "Template not found",
  "longMessage": "No template was found with slug <slug>",
  "code": "resource_not_found"
}
```

### <code><wbr />Template<wbr />Revert<wbr />Restricted</code>

`TemplateRevertRestricted` signifies an error when a custom template is attempted to be reverted

filename: Status Code: 400
```json
{
  "shortMessage": "Template revert restricted",
  "longMessage": "Template with slug <slug> can't be reverted",
  "code": "template_revert_error"
}
```

### <code><wbr />Template<wbr />Type<wbr />Unsupported</code>

`TemplateTypeUnsupported` signifies an error when an invalid template type is provided

filename: Status Code: 400
```json
{
  "shortMessage": "Template type not supported",
  "longMessage": "Template type <templateType> is not supported",
  "code": "template_type_unsupported"
}
```

## Totp

### <code><wbr />Invalid<wbr />T<wbr />O<wbr />T<wbr />P<wbr />Secret</code>

filename: Status Code: 422
```json
{
  "shortMessage": "invalid TOTP secret",
  "longMessage": "The TOTP secret is invalid, please provide a valid one base32 encoded",
  "code": "invalid_totp_secret_code"
}
```

## Urls

### <code><wbr />Insecure<wbr />U<wbr />R<wbr />L</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Insecure URL",
  "longMessage": "Please provide a secure URL (https)",
  "code": "insecure_url",
  "meta": {
    "name": "paramname"
  }
}
```

## User Settings

### <code><wbr />Attribute<wbr />At<wbr />Least<wbr />One<wbr />Must<wbr />Be<wbr />Verified<wbr />At<wbr />Sign<wbr />Up</code>

filename: Status Code: 422
```json
{
  "shortMessage": "at least one attribute must be verified on sign up",
  "longMessage": "at least one attribute must be verified on sign up because <reason>",
  "code": "attribute_at_least_one_must_be_verified_at_sign_up"
}
```

### <code><wbr />Resource<wbr />Forbidden</code>

filename: Status Code: 403
```json
{
  "shortMessage": "forbidden",
  "longMessage": "Resource forbidden",
  "code": "resource_forbidden"
}
```

### <code><wbr />Resource<wbr />Invalid</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Resource invalid",
  "longMessage": "Resource invalid",
  "code": "resource_invalid"
}
```

### <code><wbr />Resource<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "not found",
  "longMessage": "Resource not found",
  "code": "resource_not_found"
}
```

## Users

### <code><wbr />Delete<wbr />Linked<wbr />Comm<wbr />Not<wbr />Allowed</code>

`DeleteLinkedCommNotAllowed` signifies an error when trying to delete a linked communication
TODO Alex: Check if this is the correct place for this error

filename: Status Code: 400
```json
{
  "shortMessage": "Deleting a linked email address is not allowed",
  "longMessage": "This email address is linked to one or more Connected Accounts. Remove the Connected Account before deleting this email address.",
  "code": "delete_linked_identification_disallowed"
}
```

### <code><wbr />Incorrect<wbr />Password</code>

filename: Status Code: 422
```json
{
  "shortMessage": "incorrect password",
  "longMessage": "The provided password is not the one the user has set",
  "code": "incorrect_password"
}
```

### <code><wbr />Incorrect<wbr />T<wbr />O<wbr />T<wbr />P</code>

filename: Status Code: 422
```json
{
  "shortMessage": "incorrect TOTP",
  "longMessage": "The provided TOTP code is incorrect",
  "code": "totp_incorrect_code"
}
```

### <code><wbr />Invalid<wbr />Length<wbr />T<wbr />O<wbr />T<wbr />P</code>

filename: Status Code: 422
```json
{
  "shortMessage": "invalid length",
  "longMessage": "The provided TOTP code must be 6 characters long.",
  "code": "totp_invalid_length"
}
```

### <code><wbr />No<wbr />Password<wbr />Set</code>

filename: Status Code: 400
```json
{
  "shortMessage": "no password set",
  "longMessage": "This user does not have a password set for their account",
  "code": "no_password_set"
}
```

### <code><wbr />Password<wbr />Disabled</code>

filename: Status Code: 403
```json
{
  "shortMessage": "password disabled",
  "longMessage": "Password is disabled for this instance. Cannot force a password reset.",
  "code": "password_disabled"
}
```

### <code><wbr />T<wbr />O<wbr />T<wbr />P<wbr />Disabled</code>

filename: Status Code: 400
```json
{
  "shortMessage": "TOTP is disabled",
  "longMessage": "This user does not have TOTP enabled in their account",
  "code": "totp_disabled"
}
```

### <code><wbr />User<wbr />Banned</code>

`UserBanned` signifies an error when a user is banned

filename: Status Code: 403
```json
{
  "shortMessage": "User banned",
  "longMessage": "You have been banned. If you think this was by mistake, please contact support.",
  "code": "user_banned"
}
```

### <code><wbr />User<wbr />Data<wbr />Missing</code>

filename: Status Code: 422
```json
{
  "shortMessage": "missing data",
  "longMessage": "%q data doesn't match user requirements set for this instance",
  "code": "form_data_missing",
  "meta": {
    "names": "missingparams"
  }
}
```

### <code><wbr />User<wbr />Deactivated</code>

filename: Status Code: 403
```json
{
  "shortMessage": "User deactivated",
  "longMessage": "You have been deactivated. Please contact support.",
  "code": "user_deactivated"
}
```

### <code><wbr />User<wbr />Not<wbr />Found</code>

`UserNotFound` signifies an error when no user is found with userID

filename: Status Code: 404
```json
{
  "shortMessage": "not found",
  "longMessage": "No user was found with id <userID>",
  "code": "resource_not_found"
}
```

### <code><wbr />User<wbr />Quota<wbr />Exceeded</code>

filename: Status Code: 403
```json
{
  "shortMessage": "user quota exceeded",
  "longMessage": "You have reached your limit of %d users. <maxAllowed>",
  "code": "user_quota_exceeded"
}
```

### <code><wbr />User<wbr />S<wbr />C<wbr />I<wbr />M<wbr />Managed</code>

filename: Status Code: 409
```json
{
  "shortMessage": "user managed by SCIM",
  "longMessage": "This user is managed by a SCIM directory and cannot be deleted manually.",
  "code": "user_managed_by_scim"
}
```

## Waitlist

### <code><wbr />Waitlist<wbr />Entry<wbr />Locked<wbr />Error</code>

filename: Status Code: 409
```json
{
  "shortMessage": "Waitlist entry is locked",
  "longMessage": "This waitlist entry is locked and cannot be modified at this time. Please try again later.",
  "code": "waitlist_entry_locked"
}
```

## Webhooks

### <code><wbr />Svix<wbr />App<wbr />Already<wbr />Exists</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Only one Svix app is allowed per instance.",
  "longMessage": "Only one Svix app is allowed per instance.",
  "code": "svix_app_exists"
}
```

### <code><wbr />Svix<wbr />App<wbr />Create<wbr />Error</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Svix app creation failed",
  "longMessage": "Could not create a Svix app with name <name> at this time. Please contact us if this error persists.",
  "code": "svix_app_create_error"
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
