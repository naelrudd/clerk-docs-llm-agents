# Frontend API errors

An index of Clerk Frontend API errors.

## Actor Tokens

### <code><wbr />Actor<wbr />Token<wbr />Already<wbr />Used</code>

filename: Status Code: 400
```json
{
  "shortMessage": "actor token has already been used",
  "longMessage": "This actor token has already been used. Each token can only be used once.",
  "code": "actor_token_already_used_code"
}
```

### <code><wbr />Actor<wbr />Token<wbr />Can<wbr />Be<wbr />Used<wbr />Only<wbr />In<wbr />Sign<wbr />In</code>

filename: Status Code: 400
```json
{
  "shortMessage": "not in sign in",
  "longMessage": "Actor tokens can only be used during sign in.",
  "code": "actor_token_not_in_sign_in_code"
}
```

### <code><wbr />Actor<wbr />Token<wbr />Cannot<wbr />Be<wbr />Used</code>

filename: Status Code: 400
```json
{
  "shortMessage": "actor token cannot be used",
  "longMessage": "This actor token cannot be used anymore. Please request a new one.",
  "code": "actor_token_cannot_be_used_code"
}
```

### <code><wbr />Actor<wbr />Token<wbr />Revoked</code>

filename: Status Code: 400
```json
{
  "shortMessage": "actor token has been revoked",
  "longMessage": "This actor token has been revoked and cannot be used anymore.",
  "code": "actor_token_revoked_code"
}
```

### <code><wbr />Actor<wbr />Token<wbr />Subject<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "user not found",
  "longMessage": "The user of the actor token no longer exists. Please request a new one.",
  "code": "actor_token_subject_not_found"
}
```

## Agent Tasks

### <code><wbr />Agent<wbr />Task<wbr />Already<wbr />Used</code>

filename: Status Code: 400
```json
{
  "shortMessage": "agent task has already been used",
  "longMessage": "This agent task has already been used. Each task can only be used once.",
  "code": "agent_task_already_used"
}
```

### <code><wbr />Agent<wbr />Task<wbr />Can<wbr />Be<wbr />Used<wbr />Only<wbr />In<wbr />Sign<wbr />In</code>

filename: Status Code: 400
```json
{
  "shortMessage": "not in sign in",
  "longMessage": "Agent tasks can only be used during sign in.",
  "code": "agent_task_not_in_sign_in"
}
```

### <code><wbr />Agent<wbr />Task<wbr />Cannot<wbr />Be<wbr />Used</code>

filename: Status Code: 400
```json
{
  "shortMessage": "agent task cannot be used",
  "longMessage": "This agent task cannot be used anymore. Please request a new one.",
  "code": "agent_task_cannot_be_used"
}
```

### <code><wbr />Agent<wbr />Task<wbr />Revoked</code>

filename: Status Code: 400
```json
{
  "shortMessage": "agent task has been revoked",
  "longMessage": "This agent task has been revoked and cannot be used anymore.",
  "code": "agent_task_revoked"
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

## Applications

### <code><wbr />Management<wbr />Token<wbr />Subject<wbr />Not<wbr />Found</code>

`ManagementTokenSubjectNotFound` is returned when redeeming a management
token whose referenced user no longer exists in the instance.

filename: Status Code: 404
```json
{
  "shortMessage": "user not found",
  "longMessage": "The user referenced by this management token no longer exists. Mint a new token.",
  "code": "management_token_subject_not_found"
}
```

## Auth

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

### <code><wbr />Identifier<wbr />Contains<wbr />Subaddresses</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Email subaddress not allowed.",
  "longMessage": "Email address must not contain the characters '+', '=', or '#'.",
  "code": "not_allowed_access",
  "meta": {
    "name": "email_address"
  }
}
```

### <code><wbr />Identifier<wbr />From<wbr />Blocked<wbr />Country<wbr />Code</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Country code not allowed.",
  "longMessage": "Phone number sign ups are not allowed for this country code. Please use a different method.",
  "code": "not_allowed_access",
  "meta": {
    "name": "phone_number"
  }
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

### <code><wbr />Invalid<wbr />C<wbr />S<wbr />R<wbr />F<wbr />Token</code>

`InvalidCSRFToken` signifies an error when the request does not contain a CSRF token or the given token is invalid

filename: Status Code: 403
```json
{
  "shortMessage": "Invalid or missing CSRF token",
  "longMessage": "To protect against CSRF attacks, the given request must include a valid CSRF token.",
  "code": "csrf_token_invalid"
}
```

### <code><wbr />Invalid<wbr />Handshake</code>

filename: Status Code: 400
```json
{
  "shortMessage": "invalid handshake",
  "longMessage": "The handshake request is invalid: <reason>",
  "code": "invalid_handshake"
}
```

### <code><wbr />Invalid<wbr />Host</code>

`InvalidHost` signifies an error when the incoming request has an invalid host

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid host",
  "longMessage": "We were unable to attribute this request to an instance running on Clerk. Make sure that your Clerk Publishable Key is correct.",
  "code": "host_invalid"
}
```

### <code><wbr />Invalid<wbr />Origin<wbr />Header</code>

`InvalidOriginHeader` signifies an error when the origin header of the incoming request is invalid

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid HTTP Origin header",
  "longMessage": "The Request HTTP Origin header must be equal to or a subdomain of the requesting URL.",
  "code": "origin_invalid"
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

### <code><wbr />Missing<wbr />Request<wbr />Headers<wbr />For<wbr />Non<wbr />Standard<wbr />Browsers</code>

`MissingRequestHeadersForNonStandardBrowsers` signifies an error when the incoming request is missing mandatory headers

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid request headers",
  "longMessage": "Your Clerk Frontend API is accessible from browsers and native applications. To protect against common web attacks, we require the HTTP Authorization header to be present in native application requests. Make sure the HTTP Authorization header is set a valid Clerk client JWT or set it to an empty string for your first Frontend API request that will return your Clerk client JWT.",
  "code": "request_header_missing"
}
```

### <code><wbr />Missing<wbr />Request<wbr />Headers<wbr />For<wbr />Standard<wbr />Browsers</code>

`MissingRequestHeadersForStandardBrowsers` signifies an error when the incoming request is missing mandatory headers

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid request headers",
  "longMessage": "Your Clerk Frontend API is accessible from browsers and native applications. To protect against standard web attacks, the HTTP Origin header is required in browser requests. If you see this error, you probably accessed Clerk Frontend API directly from the address bar or a browser extension is intercepting your browser requests, removing the HTTP Origin header. For more information refer to https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Origin.",
  "code": "request_header_missing"
}
```

### <code><wbr />Multiple<wbr />Authorization<wbr />Header<wbr />Values</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Multiple 'Authorization' header values",
  "longMessage": "Setting multiple values in the 'Authorization' header is forbidden",
  "code": "multiple_authorization_header_values_forbidden"
}
```

### <code><wbr />Multiple<wbr />Origin<wbr />Header<wbr />Values</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Multiple 'Origin' header values",
  "longMessage": "Setting multiple values in the 'Origin' header is forbidden",
  "code": "multiple_origin_header_values_forbidden"
}
```

### <code><wbr />Native<wbr />A<wbr />P<wbr />I<wbr />Disabled</code>

`NativeAPIDisabled` signifies an error when the incoming request is from a native client (`\_is\_native={1|true}`)
and the instance is not configured to allow native API requests.

filename: Status Code: 400
```json
{
  "shortMessage": "Native API disabled",
  "longMessage": "The Native API is disabled for this instance. Visit the Clerk Dashboard to enable it.",
  "code": "native_api_disabled"
}
```

### <code><wbr />Origin<wbr />And<wbr />Authorization<wbr />Mutually<wbr />Exclusive</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Setting both the 'Origin' and 'Authorization' headers is forbidden",
  "longMessage": "For security purposes, only one of the 'Origin' and 'Authorization' headers should be provided, but not both. In browser contexts, the 'Origin' header is set automatically by the browser. In native application contexts (e.g. mobile apps), set the 'Authorization' header.",
  "code": "origin_authorization_headers_conflict"
}
```

### <code><wbr />Rate<wbr />Limited<wbr />Country</code>

supportEmail (\_) is unused here at the moment
the customer who requested this change specifically wanted to avoid adding
a support email since changing this is not in control of support.
reference: https://clerkinc.slack.com/archives/C07U96ZAZ9T/p1759344749115659?thread_ts=1758659910.343909&cid=C07U96ZAZ9T

filename: Status Code: 403
```json
{
  "shortMessage": "Rate limited country code",
  "longMessage": "SMS to the country <countryName> is temporarily disabled. Please try again later.",
  "code": "unsupported_country_code",
  "meta": "{\"Alpha2\": alpha2, \"CountryCode\": countryCode}"
}
```

### <code><wbr />Signed<wbr />Out</code>

`SignedOut` signifies an error when a user is signed out

filename: Status Code: 401
```json
{
  "shortMessage": "Signed out",
  "longMessage": "You are signed out",
  "code": "signed_out"
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

### <code><wbr />Subdomain<wbr />Not<wbr />Allowed</code>

`SubdomainNotAllowed` signifies an error when the subdomain is not in the allowlist

filename: Status Code: 403
```json
{
  "shortMessage": "Subdomain not allowed",
  "longMessage": "The request origin subdomain is not in the allowed subdomains list. Please add it to your subdomain allowlist in the Dashboard.",
  "code": "subdomain_not_allowed"
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

### <code><wbr />U<wbr />R<wbr />L<wbr />Based<wbr />Session<wbr />Syncing<wbr />Disabled</code>

`URLBasedSessionSyncingDisabled` signifies an error when the incoming request attempts
to use an endpoint with URL-based session syncing, when the instance operates with
third-party cookies instead.

filename: Status Code: 400
```json
{
  "shortMessage": "URL-based session syncing is disabled for this instance",
  "longMessage": "This is a development instance operating with legacy, third-party cookies. This feature is deprecated, please contact support if you need assistance.",
  "code": "url_based_session_syncing_disabled"
}
```

## Awscognito

### <code><wbr />Aws<wbr />Cognito<wbr />Admin<wbr />User<wbr />Password<wbr />Auth<wbr />Not<wbr />Enabled</code>

filename: Status Code: 400
```json
{
  "shortMessage": "ADMIN_USER_PASSWORD_AUTH flow not enabled for this AWS Cognito client.",
  "longMessage": "ADMIN_USER_PASSWORD_AUTH flow not enabled for this AWS Cognito client. Ensure that your Cognito user pool has a public client with the ALLOW_ADMIN_USER_PASSWORD_AUTH auth flow enabled.",
  "code": "aws_cognito_admin_user_password_auth_not_enabled"
}
```

### <code><wbr />Aws<wbr />Cognito<wbr />User<wbr />Lambda<wbr />Validation<wbr />Failed</code>

filename: Status Code: 422
```json
{
  "shortMessage": "AWS Cognito user validation failed.",
  "longMessage": "The sign-in attempt was rejected by the AWS Cognito user validation Lambda trigger.",
  "code": "aws_cognito_user_lambda_validation_failed"
}
```

### <code><wbr />Aws<wbr />Cognito<wbr />User<wbr />Password<wbr />Auth<wbr />Not<wbr />Enabled</code>

filename: Status Code: 400
```json
{
  "shortMessage": "USER_PASSWORD_AUTH flow not enabled for this AWS Cognito client.",
  "longMessage": "USER_PASSWORD_AUTH flow not enabled for this AWS Cognito client. Ensure that your Cognito user pool has a public client with the ALLOW_USER_PASSWORD_AUTH auth flow enabled.",
  "code": "aws_cognito_user_password_auth_not_enabled"
}
```

## Backup Codes

### <code><wbr />Backup<wbr />Codes<wbr />Not<wbr />Available</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Backup codes not available",
  "longMessage": "In order to use backup codes, you have to enable any other Multi-factor method",
  "code": "backup_codes_not_available"
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

### <code><wbr />Annual<wbr />Plan<wbr />Period<wbr />Not<wbr />Supported</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Annual plan period not supported",
  "longMessage": "Annual plan period not supported",
  "code": "annual_plan_period_not_supported"
}
```

### <code><wbr />Billing<wbr />Not<wbr />Enabled</code>

filename: Status Code: 403
```json
{
  "shortMessage": "access denied",
  "longMessage": "The billing feature is not enabled for this instance. You can enable it at https://dashboard.clerk.com.",
  "code": "billing_not_enabled"
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

### <code><wbr />Billing<wbr />Plan<wbr />Is<wbr />Hidden</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Plan is not Publicly available",
  "longMessage": "Plan is not Publicly available, and should not be used in checkout",
  "code": "billing_plan_is_hidden"
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

### <code><wbr />Checkout<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "Checkout not found",
  "longMessage": "Checkout not found",
  "code": "checkout_not_found"
}
```

### <code><wbr />Commerce<wbr />Statement<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "Statement not found",
  "longMessage": "No statement found with id <statementID>.",
  "code": "commerce_statement_not_found"
}
```

### <code><wbr />External<wbr />Payments<wbr />Not<wbr />Setup</code>

filename: Status Code: 422
```json
{
  "shortMessage": "External payments not setup",
  "longMessage": "External payments not setup",
  "code": "external_payments_not_setup"
}
```

### <code><wbr />Invalid<wbr />Gateway<wbr />Type</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid gateway type",
  "longMessage": "Gateway type is invalid",
  "code": "invalid_gateway_type"
}
```

### <code><wbr />Invalid<wbr />Plan<wbr />Change</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid plan change",
  "longMessage": "Please choose a different plan or billing interval, or contact support.",
  "code": "invalid_plan_change",
  "meta": "{\"Plan\": {\"ID\": \"planID\", \"Name\": \"planName\", \"CurrencySymbol\": \"currencySymbol\", \"AmountFormatted\": \"amountFormatted\", \"AnnualAmountFormatted\": \"annualMonthlyAmountFormatted\"}, \"Period\": period, \"IsPlanUpgradePossible\": isPlanUpgradePossible}"
}
```

### <code><wbr />Invalid<wbr />Plan<wbr />Type</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Invalid plan type",
  "longMessage": "Plan type (<planType>) is invalid",
  "code": "invalid_plan_type"
}
```

### <code><wbr />Invalid<wbr />Use<wbr />Of<wbr />Test<wbr />Card</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid use of test card",
  "longMessage": "Test card cannot be used in production environment.",
  "code": "invalid_use_of_test_card"
}
```

### <code><wbr />Max<wbr />Payment<wbr />Sources<wbr />Quota<wbr />Exceeded</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Max payment methods quota exceeded",
  "longMessage": "You have reached your limit of %d payment methods. Please delete a payment source to add a new one.",
  "code": "max_payment_methods_quota_exceeded"
}
```

### <code><wbr />Missing<wbr />Payer<wbr />Email</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Missing payer email",
  "longMessage": "Payer email is required to perform this operation",
  "code": "missing_payer_email"
}
```

### <code><wbr />Missing<wbr />Plan<wbr />I<wbr />D</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Missing plan ID",
  "longMessage": "Plan ID is required to perform this operation",
  "code": "missing_plan_id"
}
```

### <code><wbr />Monthly<wbr />Plan<wbr />Period<wbr />Not<wbr />Supported</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Monthly plan period not supported",
  "longMessage": "Monthly plan period not supported",
  "code": "monthly_plan_period_not_supported"
}
```

### <code><wbr />Org<wbr />Member<wbr />Limit<wbr />Exceeded<wbr />For<wbr />Plan<wbr />Change</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Organization member limit exceeded",
  "longMessage": "Plan change is not allowed because the organization's <occupiedSeatsStr> occupied seats exceed the limit of <maxAllowedStr> organization memberships.",
  "code": "org_member_limit_exceeded_for_plan_change"
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

### <code><wbr />Payer<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "Payer not found",
  "longMessage": "Payer not found",
  "code": "payer_not_found"
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

### <code><wbr />Payment<wbr />Source<wbr />Expired</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Payment method is expired",
  "longMessage": "Payment method is expired",
  "code": "payment_source_expired"
}
```

### <code><wbr />Payment<wbr />Source<wbr />In<wbr />Use</code>

filename: Status Code: 409
```json
{
  "shortMessage": "Payment source in use",
  "longMessage": "Payment source is in use, as you have active subscriptions. Please cancel those subscriptions before deleting the payment source.",
  "code": "payment_source_in_use"
}
```

### <code><wbr />Payment<wbr />Source<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "Payment source not found",
  "longMessage": "Payment source not found",
  "code": "payment_source_not_found"
}
```

### <code><wbr />Plan<wbr />Already<wbr />Active</code>

filename: Status Code: 409
```json
{
  "shortMessage": "Plan already active",
  "longMessage": "Plan already active",
  "code": "plan_already_active"
}
```

### <code><wbr />Plan<wbr />Cannot<wbr />Have<wbr />Seats</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Plan cannot have seats",
  "longMessage": "The selected plan is not seat-based, but the checkout request included a seat_quantity.",
  "code": "plan_cannot_have_seats"
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

### <code><wbr />Plan<wbr />Seat<wbr />Limit<wbr />Exceeded</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Plan seat limit exceeded",
  "longMessage": "Your organization has <currentMembersStr> members, but the requested plan would only support <seatLimitStr> members. Please remove members before switching to this plan.",
  "code": "plan_seat_limit_exceeded",
  "meta": "{\"PlanSeatLimit\": planSeatLimit, \"CurrentMembers\": currentMembers}"
}
```

### <code><wbr />Price<wbr />I<wbr />D<wbr />Invalid<wbr />For<wbr />Checkout</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Invalid price_id for checkout",
  "longMessage": "You cannot checkout with that price.",
  "code": "price_id_invalid_for_checkout"
}
```

### <code><wbr />Requested<wbr />Seats<wbr />Insufficient</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Requested seats insufficient",
  "longMessage": "Your organization has <currentMembersStr> members but this checkout only grants <grantedSeatsStr> seats. Please request at least <currentMembersStr> seats or remove members.",
  "code": "requested_seats_insufficient",
  "meta": "{\"PlanSeatLimit\": grantedSeats, \"CurrentMembers\": currentMembers}"
}
```

### <code><wbr />Seat<wbr />Based<wbr />Billing<wbr />Exceeds<wbr />Org<wbr />Member<wbr />Limit</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Seat-based billing exceeds plan's organization member limit",
  "longMessage": "The seat-based plan you are trying to create exceeds your Clerk plan's organization member limit. Adjust your seat limits to match your plan's limit or upgrade your subscription.",
  "code": "seat_based_billing_exceeds_org_member_limit"
}
```

### <code><wbr />Seat<wbr />Reduction<wbr />In<wbr />Checkout<wbr />Not<wbr />Supported</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Seat reduction not supported in checkout",
  "longMessage": "Seats cannot be reduced through checkout.",
  "code": "seat_reduction_in_checkout_not_supported"
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

## Domains

### <code><wbr />Operation<wbr />Not<wbr />Allowed<wbr />On<wbr />Satellite<wbr />Domain</code>

filename: Status Code: 403
```json
{
  "shortMessage": "operation not allowed",
  "longMessage": "This operation is not allowed on a satellite domain. Try again using the primary domain of your instance.",
  "code": "operation_not_allowed_on_satellite_domain"
}
```

### <code><wbr />Sync<wbr />Nonce<wbr />Already<wbr />Consumed</code>

`SyncNonceAlreadyConsumed` signifies an error when the nonce that was given
during the sync flow is already consumed.

filename: Status Code: 403
```json
{
  "shortMessage": "sync nonce already consumed",
  "longMessage": "The given sync nonce has already been consumed and cannot be re-used.",
  "code": "sync_nonce_already_consumed"
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

## Enterprise Sso

### <code><wbr />Enterprise<wbr />Connection<wbr />Invalid<wbr />Type</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid enterprise connection type",
  "longMessage": "The enterprise connection type is not supported.",
  "code": "enterprise_connection_invalid_type"
}
```

### <code><wbr />Enterprise<wbr />S<wbr />S<wbr />O<wbr />Account<wbr />Already<wbr />Connected<wbr />With<wbr />Email</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Already connected",
  "longMessage": "An enterprise account is already connected for this connection email: <email>",
  "code": "enterprise_sso_account_already_connected"
}
```

### <code><wbr />Enterprise<wbr />S<wbr />S<wbr />O<wbr />Additional<wbr />Identifications<wbr />Disabled</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Identifications creation disabled by your enterprise account",
  "longMessage": "You cannot create identifications because your enterprise account does not allow it.",
  "code": "enterprise_sso_additional_identifications_disabled"
}
```

### <code><wbr />Enterprise<wbr />S<wbr />S<wbr />O<wbr />Email<wbr />Address<wbr />Domain<wbr />Mismatch</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Enterprise Connection email address domain mismatch",
  "longMessage": "The email address returned by the provider <received> does not match the domain of the enterprise connection <expected> that initiated the authentication.",
  "code": "enterprise_sso_email_address_domain_mismatch",
  "meta": {
    "expecteddomain": "expected",
    "receiveddomain": "received"
  }
}
```

### <code><wbr />Enterprise<wbr />S<wbr />S<wbr />O<wbr />Hosted<wbr />Domain<wbr />Mismatch</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Hosted domain mismatch",
  "longMessage": "The Enterprise Connection domain does not match the user's hosted domain from the OAuth provider.",
  "code": "enterprise_sso_hosted_domain_mismatch"
}
```

### <code><wbr />Enterprise<wbr />S<wbr />S<wbr />O<wbr />Sign<wbr />Up<wbr />Connection<wbr />Missing</code>

filename: Status Code: 422
```json
{
  "shortMessage": "No Enterprise Connection for this sign-up",
  "longMessage": "The current sign-up does not have a corresponding Enterprise Connection. Please check the domain of the provided email address.",
  "code": "enterprise_sso_sign_up_connection_missing"
}
```

### <code><wbr />Enterprise<wbr />S<wbr />S<wbr />O<wbr />User<wbr />Attribute<wbr />Missing</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Enterprise Connection user attribute missing",
  "longMessage": "This account does not have an associated '<attrName>' attribute. Contact the IdP administrator for resolution.",
  "code": "enterprise_sso_user_attribute_missing",
  "meta": {
    "missingattribute": "attrname"
  }
}
```

## Features

### <code><wbr />Feature<wbr />Not<wbr />Enabled</code>

filename: Status Code: 403
```json
{
  "shortMessage": "not enabled",
  "longMessage": "This feature is not enabled on this instance",
  "code": "feature_not_enabled"
}
```

### <code><wbr />Feature<wbr />Requires<wbr />Dynamic<wbr />Oauth<wbr />Client<wbr />Registration</code>

filename: Status Code: 422
```json
{
  "shortMessage": "dynamic client registration is not enabled",
  "longMessage": "Dynamic client registration is not enabled on this instance. Please enable it in the instance settings to use this feature",
  "code": "feature_requires_dynamic_oauth_client_registration"
}
```

### <code><wbr />Feature<wbr />Requires<wbr />Email<wbr />Address<wbr />Attribute<wbr />Enabled</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Email address attribute must be enabled",
  "longMessage": "This feature requires the email address attribute to be enabled. Please enable it in your instance settings to continue.",
  "code": "feature_requires_email_address_enabled"
}
```

### <code><wbr />Feature<wbr />Requires<wbr />End<wbr />Session<wbr />Enabled</code>

filename: Status Code: 400
```json
{
  "shortMessage": "End session feature is not enabled",
  "longMessage": "The end session feature is not enabled for this instance. Please contact support to enable this feature",
  "code": "feature_requires_end_session_enabled"
}
```

### <code><wbr />Feature<wbr />Requires<wbr />O<wbr />Auth2<wbr />Consent<wbr />Screen<wbr />Enabled</code>

filename: Status Code: 422
```json
{
  "shortMessage": "OAuth Client does not have the consent screen enabled",
  "longMessage": "OAuth Client does not have the consent screen enabled, please enable it in the OAuth Client settings to use this feature",
  "code": "feature_requires_oauth2_consent_screen_enabled"
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

## Forms

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

### <code><wbr />Form<wbr />Disabled<wbr />Parameter<wbr />Value</code>

`FormDisabledParameterValue` signifies an error when the given parameter has an invalid value because it is not enabled in the settings

filename: Status Code: 400
```json
{
  "shortMessage": "is disabled",
  "longMessage": "<value> is disabled. Please verify you're using the correct instance, or see our docs to learn how to enable this value.",
  "code": "form_param_value_disabled",
  "meta": {
    "name": "param"
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

### <code><wbr />Form<wbr />Identifier<wbr />Not<wbr />Found</code>

`FormIdentifierNotFound` signifies an error when a required identifier is not found

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_identifier_not_found",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Incorrect<wbr />Code</code>

`FormIncorrectCode` signifies an error when the given code is incorrect

filename: Status Code: 422
```json
{
  "shortMessage": "is incorrect",
  "longMessage": "Incorrect code",
  "code": "form_code_incorrect",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Incorrect<wbr />Signature</code>

filename: Status Code: 422
```json
{
  "shortMessage": "is incorrect",
  "longMessage": "Incorrect signature",
  "code": "form_incorrect_signature"
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

### <code><wbr />Form<wbr />Invalid<wbr />Email<wbr />Addresses</code>

filename: Status Code: 422
```json
{
  "shortMessage": "invalid email addresses",
  "longMessage": "The following email addresses are invalid: <emailAddresses>",
  "code": "form_param_format_invalid",
  "meta": {
    "emailaddresses": "invalidemailaddresses"
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

### <code><wbr />Form<wbr />Legal<wbr />Not<wbr />Accepted</code>

FormDisabledParameterValue signifies an error when the legal consent value has not been filled

filename: Status Code: 422
```json
{
  "shortMessage": "legal not accepted",
  "longMessage": "Legal consent must be accepted in order to continue.",
  "code": "legal_not_accepted",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Maximum<wbr />Parameters<wbr />Exceeded</code>

`FormMaximumParametersExceeded` signifies an error when more than 100 of the same param is included.

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "longMessage": "<param> is included more than the maximum of 100 times.",
  "code": "form_param_duplicate",
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

### <code><wbr />Form<wbr />New<wbr />Password<wbr />Matches<wbr />Current</code>

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "New password cannot be the same as the current password.",
  "code": "form_new_password_matches_current",
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

### <code><wbr />Form<wbr />Nil<wbr />Parameter<wbr />With<wbr />Custom<wbr />Text</code>

`FormNilParameterWithCustomText` signifies an error when a nil parameter is found in a form.
This variant also accepts a custom text to be displayed.

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

### <code><wbr />Form<wbr />Password<wbr />Compromised</code>

`FormPasswordCompromised` signifies an error when the chosen password has been found in the pwned list

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "longMessage": "Your password may be compromised. To protect your account, please continue with an alternative sign-in method. You will be required to reset your password after signing in.",
  "code": "form_password_compromised",
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

### <code><wbr />Form<wbr />Password<wbr />Incorrect</code>

`FormPasswordIncorrect` signifies an error when given password is incorrect

filename: Status Code: 422
```json
{
  "shortMessage": "Password is incorrect. Try again, or use another method.",
  "longMessage": "Password is incorrect. Try again, or use another method.",
  "code": "form_password_incorrect",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Form<wbr />Password<wbr />Or<wbr />Identifier<wbr />Incorrect</code>

`FormPasswordOrIdentifierIncorrect` signifies an error when given password
is incorrect or given identifier does not match an existing account, but does
not return which is incorrect. This is used with enumeration protection.

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "form_password_or_identifier_incorrect"
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

### <code><wbr />Form<wbr />Unknown<wbr />Parameter</code>

`FormUnknownParameter` signifies an error when an unexpected parameter is found in a form

filename: Status Code: 422
```json
{
  "shortMessage": "is unknown",
  "longMessage": "<param> is not a valid parameter for this request.",
  "code": "form_param_unknown",
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

### <code><wbr />Device<wbr />Attestation<wbr />Challenge<wbr />Client<wbr />Mismatch</code>

filename: Status Code: 401
```json
{
  "shortMessage": "device attestation challenge client mismatch",
  "longMessage": "The device attestation challenge provided is not valid for the client.",
  "code": "device_attestation_challenge_client_mismatch"
}
```

### <code><wbr />Device<wbr />Attestation<wbr />Misconfigured</code>

filename: Status Code: 401
```json
{
  "shortMessage": "device attestation is misconfigured",
  "longMessage": "Device attestation is misconfigured for this instance.",
  "code": "device_attestation_misconfigured"
}
```

### <code><wbr />Device<wbr />Attestation<wbr />Not<wbr />Configured</code>

filename: Status Code: 401
```json
{
  "shortMessage": "device attestation not configured",
  "longMessage": "Device attestation is not configured for this instance.",
  "code": "device_attestation_not_configured"
}
```

### <code><wbr />Device<wbr />Attestation<wbr />Unsupported<wbr />Platform</code>

filename: Status Code: 401
```json
{
  "shortMessage": "unsupported native client platform",
  "longMessage": "Device attestation is not supported for the client platform.",
  "code": "device_attestation_unsupported_platform"
}
```

### <code><wbr />Device<wbr />Attestation<wbr />Verification<wbr />Failed</code>

filename: Status Code: 401
```json
{
  "shortMessage": "device attestation verification failed",
  "longMessage": "Failed to verify the provided device attestation.",
  "code": "device_attestation_verification_failed"
}
```

### <code><wbr />Fraud<wbr />Action<wbr />Blocked</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Action blocked",
  "longMessage": "This action was detected as suspicious and has been blocked. If you believe this was a mistake, please contact support.",
  "code": "action_blocked"
}
```

### <code><wbr />Fraud<wbr />Device<wbr />Blocked</code>

filename: Status Code:&#x20;
```json
{
  "shortMessage": "Device blocked",
  "longMessage": "This device was detected as suspicious and has been blocked. It will no longer be able to perform actions. If you believe this was by mistake, please contact support.",
  "code": "device_blocked"
}
```

### <code><wbr />Fraud<wbr />Rate<wbr />Limit<wbr />Exceeded</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Unusual activity was detected",
  "longMessage": "Unusual activity was detected. Please try again later or contact our support if you continue to experience issues.",
  "code": "captcha_invalid"
}
```

### <code><wbr />Fraud<wbr />Sign<wbr />Up<wbr />Rate<wbr />Limit<wbr />Exceeded</code>

filename: Status Code: 429
```json
{
  "shortMessage": "Sign up rate limit exceeded",
  "longMessage": "The sign up rate limit was exceeded. Please try a different method or contact our support if you continue to experience issues.",
  "code": "signup_rate_limit_exceeded"
}
```

### <code><wbr />Invalid<wbr />Device<wbr />Attestation<wbr />Assertion</code>

filename: Status Code: 401
```json
{
  "shortMessage": "invalid device attestation assertion",
  "longMessage": "The device attestation assertion provided is invalid.",
  "code": "invalid_device_attestation_assertion"
}
```

### <code><wbr />Invalid<wbr />Device<wbr />Attestation<wbr />Challenge</code>

filename: Status Code: 401
```json
{
  "shortMessage": "invalid device attestation challenge",
  "longMessage": "The device attestation challenge provided is either invalid or has expired.",
  "code": "invalid_device_attestation_challenge"
}
```

### <code><wbr />Protect<wbr />Check<wbr />Already<wbr />Resolved</code>

filename: Status Code: 400
```json
{
  "shortMessage": "protect check already resolved",
  "longMessage": "This protect check has already been completed and cannot be resolved again.",
  "code": "protect_check_already_resolved"
}
```

### <code><wbr />Requires<wbr />Device<wbr />Attestation</code>

filename: Status Code: 401
```json
{
  "shortMessage": "Device attestation is required",
  "longMessage": "A valid device attestation could not be found for the client.",
  "code": "requires_device_attestation"
}
```

## Google One Tap

### <code><wbr />Google<wbr />One<wbr />Tap<wbr />Token<wbr />Invalid</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Google One Tap token is invalid",
  "longMessage": "The provided Google One Tap token is invalid. Make sure you're using a valid token generated by Google.",
  "code": "google_one_tap_token_invalid"
}
```

## Identifications

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

### <code><wbr />Immutable<wbr />Attribute<wbr />Modification<wbr />Not<wbr />Allowed</code>

filename: Status Code: 403
```json
{
  "shortMessage": "",
  "longMessage": "Your <sanitizedAttributeType> is immutable and cannot be modified or removed.",
  "code": "immutable_attribute_modification_not_allowed"
}
```

### <code><wbr />O<wbr />Auth<wbr />Connection<wbr />Blocked<wbr />By<wbr />Immutable<wbr />Attribute</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Cannot connect account",
  "longMessage": "This account cannot be connected because its <sanitizedAttributeType> does not match your existing <sanitizedAttributeType>.",
  "code": "oauth_connection_blocked_by_immutable_attribute"
}
```

### <code><wbr />Second<wbr />Factor<wbr />Deletion<wbr />Not<wbr />Allowed</code>

filename: Status Code: 400
```json
{
  "shortMessage": "second factor deletion not allowed",
  "longMessage": "You are required to maintain at least one two-step verification method in your account at all times",
  "code": "second_factor_deletion_not_allowed"
}
```

### <code><wbr />Too<wbr />Many<wbr />Unverified<wbr />Identifications</code>

filename: Status Code: 400
```json
{
  "shortMessage": "too many unverified contacts",
  "longMessage": "There are too many unverified contacts for this user.",
  "code": "too_many_unverified_identifications"
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

## Instances

### <code><wbr />Instance<wbr />Type<wbr />Invalid</code>

`InstanceTypeInvalid` signifies an error when a request cannot be applied to the given instance

filename: Status Code: 400
```json
{
  "shortMessage": "This request isn't valid for this instance type.",
  "longMessage": "This request isn't valid for this instance type.",
  "code": "instance_type_invalid"
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

### <code><wbr />Invitation<wbr />Account<wbr />Already<wbr />Exists</code>

`InvitationAccountAlreadyExists` denotes an error when there is an existing
user identification with the same email as the invitation.

filename: Status Code: 400
```json
{
  "shortMessage": "account exists",
  "longMessage": "An account already exists for this invitation. Sign in instead.",
  "code": "invitation_account_exists"
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

### <code><wbr />Invitation<wbr />Identification<wbr />Not<wbr />Exist</code>

filename: Status Code: 400
```json
{
  "shortMessage": "identification not found",
  "longMessage": "This invitation refers to a non-existing identification.",
  "code": "invitation_account_not_exists"
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

## Native Magic Link

### <code><wbr />Native<wbr />Magic<wbr />Link<wbr />Approval<wbr />Token<wbr />Consumed</code>

filename: Status Code: 422
```json
{
  "shortMessage": "approval token consumed",
  "longMessage": "The approval token has already been used.",
  "code": "approval_token_consumed"
}
```

### <code><wbr />Native<wbr />Magic<wbr />Link<wbr />Approval<wbr />Token<wbr />Expired</code>

filename: Status Code: 422
```json
{
  "shortMessage": "approval token expired",
  "longMessage": "The approval token has expired. Please request a new email link.",
  "code": "approval_token_expired"
}
```

### <code><wbr />Native<wbr />Magic<wbr />Link<wbr />Approval<wbr />Token<wbr />Invalid</code>

filename: Status Code: 422
```json
{
  "shortMessage": "approval token invalid",
  "longMessage": "The approval token is invalid.",
  "code": "approval_token_invalid"
}
```

### <code><wbr />Native<wbr />Magic<wbr />Link<wbr />P<wbr />K<wbr />C<wbr />E<wbr />Verification<wbr />Failed</code>

filename: Status Code: 422
```json
{
  "shortMessage": "PKCE verification failed",
  "longMessage": "The provided code verifier does not match the prepared code challenge.",
  "code": "pkce_verification_failed"
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

### <code><wbr />External<wbr />Account<wbr />Not<wbr />Found</code>

`ExternalAccountNotFound` signifies an error when the external account of the oauth callback is not found
NOTE: This legacy error message and code is misleading. We also throw this error in transfer flows
where an external account was created, but no corresponding user has yet been created.

filename: Status Code: 404
```json
{
  "shortMessage": "Invalid external account",
  "longMessage": "The External Account was not found.",
  "code": "external_account_not_found"
}
```

### <code><wbr />Invalid<wbr />O<wbr />Auth<wbr />Callback</code>

`InvalidOAuthCallback` signifies an error when the form of OAuth callback is invalid

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid OAuth callback",
  "longMessage": "invalid form for oauth_callback",
  "code": "oauth_callback_invalid"
}
```

### <code><wbr />Misconfigured<wbr />O<wbr />Auth<wbr />Provider</code>

`MisconfiguredOAuthProvider` signifies an error when there is a misconfiguration for an OAuth provider

filename: Status Code: 400
```json
{
  "shortMessage": "Misconfigured OAuth provider",
  "longMessage": "Misconfigured OAuth provider. Please make sure you have set it correctly",
  "code": "misconfigured_oauth_provider"
}
```

### <code><wbr />Non<wbr />Authenticatable<wbr />Oauth<wbr />Provider</code>

`NonAuthenticatableOauthProvider` signifies an error when an oauth flow step is attempted for a provider that is not
enabled for authentication.

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "%v OAuth is not supported for authentication. Please contact us if you think this error should not appear.",
  "code": "oauth_non_authenticatable_provider"
}
```

### <code><wbr />O<wbr />Auth<wbr />Access<wbr />Denied</code>

filename: Status Code: 403
```json
{
  "shortMessage": "",
  "longMessage": "You did not grant access to your <providerName> account",
  "code": "oauth_access_denied"
}
```

### <code><wbr />O<wbr />Auth<wbr />Account<wbr />Already<wbr />Connected</code>

`OAuthAccountAlreadyConnected` signifies an error when an OAuth account if already connected for a specific provider

filename: Status Code: 400
```json
{
  "shortMessage": "Already connected",
  "longMessage": "Another account is already connected for this particular provider (<providerTitle>)",
  "code": "oauth_account_already_connected"
}
```

### <code><wbr />O<wbr />Auth<wbr />Config<wbr />Missing</code>

`OAuthConfigMissing` signifies an error when an application does not have
SSO credentials set, for a particular SSO provider.

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "The application does not have <provider> OAuth keys set in its settings.",
  "code": "oauth_config_missing"
}
```

### <code><wbr />O<wbr />Auth<wbr />Fetch<wbr />User<wbr />Error</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Fetch user error",
  "longMessage": "Fetch user error",
  "code": "oauth_fetch_user_error"
}
```

### <code><wbr />O<wbr />Auth<wbr />Identification<wbr />Claimed</code>

`OAuthIdentificationClaimed` signifies an error when the requested oauth identification is already claimed by another user

filename: Status Code: 400
```json
{
  "shortMessage": "Identification claimed by another user",
  "longMessage": "The email address associated with this OAuth account is already claimed by another user.",
  "code": "oauth_identification_claimed"
}
```

### <code><wbr />O<wbr />Auth<wbr />Invalid<wbr />Redirect<wbr />U<wbr />R<wbr />I</code>

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "Your <providerName> account configuration is invalid. Make sure you register this endpoint in the list of allowed callback URLs.",
  "code": "redirect_uri_mismatch"
}
```

### <code><wbr />O<wbr />Auth<wbr />Malformed<wbr />Redirect<wbr />U<wbr />R<wbr />I</code>

filename: Status Code: 400
```json
{
  "shortMessage": "malformed redirect uri provided",
  "longMessage": "malformed redirect uri provided",
  "code": "redirect_uri_mismatch"
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

### <code><wbr />O<wbr />Auth<wbr />Provider<wbr />Not<wbr />Enabled</code>

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "Single-sign on with <providerTitle> OAuth provider is not enabled in the instance settings.",
  "code": "oauth_provider_not_enabled"
}
```

### <code><wbr />O<wbr />Auth<wbr />Shared<wbr />Credentials<wbr />Not<wbr />Supported</code>

`OAuthSharedCredentialsNotSupported` signifies an error when an OAuth provider uses our shared credentials, but those are not supported anymore.

filename: Status Code: 400
```json
{
  "shortMessage": "Shared credentials not supported",
  "longMessage": "Shared credentials are no longer supported for this provider. Please update via the Clerk Dashboard.",
  "code": "oauth_shared_credentials_not_supported"
}
```

### <code><wbr />O<wbr />Auth<wbr />Token<wbr />Exchange<wbr />Error</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Token exchange error",
  "longMessage": "Token exchange error",
  "code": "oauth_token_exchange_error"
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

## Oauth2 Idp

### <code><wbr />O<wbr />Auth<wbr />Fetch<wbr />User<wbr />Info</code>

`OAuthFetchUserInfo` signifies an error when user info cannot be retrieved with the access token

filename: Status Code: 401
```json
{
  "shortMessage": "unable to fetch user info",
  "longMessage": "Unable to fetch user info. Check if access token is present and valid.",
  "code": "oauth_fetch_user_error"
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

### <code><wbr />Invitations<wbr />Not<wbr />Supported<wbr />In<wbr />Organization</code>

filename: Status Code: 403
```json
{
  "shortMessage": "email invitations not supported",
  "longMessage": "This organization doesn't support email invitations. Please contact support to enable this feature.",
  "code": "invitations_not_supported_in_organization"
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

### <code><wbr />Organization<wbr />Admin<wbr />Delete<wbr />Not<wbr />Enabled</code>

filename: Status Code: 403
```json
{
  "shortMessage": "admin delete not enabled",
  "longMessage": "Deletion by admin is not enabled for this organization.",
  "code": "organization_admin_delete_not_enabled"
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

### <code><wbr />Organization<wbr />Domain<wbr />Mismatch</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Organization domain mismatch",
  "longMessage": "The provided email address doesn't match the organization domain name.",
  "code": "organization_domain_mismatch",
  "meta": {
    "name": "param"
  }
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

### <code><wbr />Organization<wbr />Invitation<wbr />Already<wbr />Accepted</code>

filename: Status Code: 400
```json
{
  "shortMessage": "invitation has already been accepted",
  "longMessage": "This invitation has already been accepted. Sign in instead.",
  "code": "organization_invitation_already_accepted"
}
```

### <code><wbr />Organization<wbr />Invitation<wbr />Identification<wbr />Already<wbr />Exists</code>

filename: Status Code: 400
```json
{
  "shortMessage": "email address already exists",
  "longMessage": "The email address in this invitation already exists. If it belongs to you, try signing in instead.",
  "code": "organization_invitation_identification_already_exists"
}
```

### <code><wbr />Organization<wbr />Invitation<wbr />Identification<wbr />Not<wbr />Exist</code>

filename: Status Code: 400
```json
{
  "shortMessage": "identification not found",
  "longMessage": "User not found. If you don't have an account, sign up first to accept this invitation.",
  "code": "organization_invitation_identification_not_exist"
}
```

### <code><wbr />Organization<wbr />Invitation<wbr />Not<wbr />Found</code>

404 - Invitation not found.

filename: Status Code: 404
```json
{
  "shortMessage": "not found",
  "longMessage": "No invitation found with id <invitationID>.",
  "code": "organization_invitation_not_found"
}
```

### <code><wbr />Organization<wbr />Invitation<wbr />Not<wbr />Pending</code>

404 - Invitation is not pending.

filename: Status Code: 404
```json
{
  "shortMessage": "not pending",
  "longMessage": "The organization invitation is not in the 'pending' status.",
  "code": "organization_invitation_not_pending"
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

### <code><wbr />Organization<wbr />Invitation<wbr />Revoked</code>

filename: Status Code: 400
```json
{
  "shortMessage": "invitation has been revoked",
  "longMessage": "This invitation has been revoked and cannot be used anymore.",
  "code": "organization_invitation_revoked_code"
}
```

### <code><wbr />Organization<wbr />Invitation<wbr />To<wbr />Deleted<wbr />Organization</code>

filename: Status Code: 400
```json
{
  "shortMessage": "organization invitation to deleted organization",
  "longMessage": "This invitation refers to an organization that has been deleted.",
  "code": "organization_invitation_to_deleted_organization"
}
```

### <code><wbr />Organization<wbr />Managed<wbr />Role<wbr />Operation<wbr />F<wbr />A<wbr />P<wbr />I<wbr />Disallowed</code>

filename: Status Code: 422
```json
{
  "shortMessage": "organization managed role operation disallowed",
  "longMessage": "Managed roles cannot be set through the frontend API. Use the dashboard or backend API instead.",
  "code": "form_param_value_invalid",
  "meta": {
    "name": "paramname"
  }
}
```

### <code><wbr />Organization<wbr />Membership<wbr />Enterprise<wbr />Connection<wbr />Cannot<wbr />Remove</code>

filename: Status Code: 403
```json
{
  "shortMessage": "cannot remove enterprise connection organization membership",
  "longMessage": "Cannot remove an organization membership that is tied to an enterprise connection.",
  "code": "organization_membership_enterprise_connection_cannot_remove"
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

### <code><wbr />Organization<wbr />Suggestion<wbr />Already<wbr />Accepted</code>

filename: Status Code: 400
```json
{
  "shortMessage": "suggestion has already been accepted",
  "longMessage": "This organization suggestion has already been accepted.",
  "code": "organization_suggestion_already_accepted"
}
```

### <code><wbr />Organization<wbr />Unlimited<wbr />Memberships<wbr />Required</code>

filename: Status Code: 403
```json
{
  "shortMessage": "organization has limited memberships",
  "longMessage": "This feature is not supported because organization membership is limited. You can remove the limit by enabling unlimited memberships.",
  "code": "organization_unlimited_membership_required"
}
```

### <code><wbr />Organization<wbr />Unlimited<wbr />Memberships<wbr />Upgrade<wbr />Required</code>

filename: Status Code: 403
```json
{
  "shortMessage": "organization has limited memberships",
  "longMessage": "This feature is not supported because organization membership is limited. You can remove the limit by upgrading your subscription plan.",
  "code": "organization_unlimited_membership_required"
}
```

## Passkeys

### <code><wbr />Passkey<wbr />Authentication<wbr />Failure</code>

filename: Status Code: 400
```json
{
  "shortMessage": "authentication failed",
  "longMessage": "Passkey authentication failed",
  "code": "passkey_authentication_failure"
}
```

### <code><wbr />Passkey<wbr />Identification<wbr />Not<wbr />Verified</code>

filename: Status Code: 422
```json
{
  "shortMessage": "passkey identification not verified",
  "longMessage": "Passkey identification not verified. Registration is incomplete.",
  "code": "passkey_identification_not_verified"
}
```

### <code><wbr />Passkey<wbr />Invalid<wbr />Public<wbr />Key<wbr />Credential</code>

filename: Status Code: 422
```json
{
  "shortMessage": "is invalid",
  "longMessage": "Invalid passkey public key credential",
  "code": "passkey_invalid_public_key_credential",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />Passkey<wbr />Invalid<wbr />Verification</code>

filename: Status Code: 400
```json
{
  "shortMessage": "invalid verification",
  "longMessage": "Passkey verification contains invalid nonce",
  "code": "passkey_invalid_verification"
}
```

### <code><wbr />Passkey<wbr />Not<wbr />Registered</code>

filename: Status Code: 404
```json
{
  "shortMessage": "not registered",
  "longMessage": "Passkey is not registered.",
  "code": "passkey_not_registered"
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

## Redirect Urls

### <code><wbr />Invalid<wbr />Redirect<wbr />U<wbr />R<wbr />L</code>

`InvalidRedirectURL` signifies an error when a RedirectURL is in invalid format

filename: Status Code: 422
```json
{
  "shortMessage": "Redirect url invalid",
  "longMessage": "The provided redirect url is not in a valid format",
  "code": "invalid_redirect_url"
}
```

### <code><wbr />Prohibited<wbr />Redirect<wbr />U<wbr />R<wbr />L<wbr />Scheme</code>

ProhibitedRedirectURL signifies that the redirect url scheme is prohibited

filename: Status Code: 422
```json
{
  "shortMessage": "Invalid URL scheme",
  "longMessage": "The provided redirect url has a prohibited URL scheme",
  "code": "prohibited_redirect_url"
}
```

### <code><wbr />Redirect<wbr />U<wbr />R<wbr />L<wbr />Domain<wbr />Mismatch</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Redirect url does not belong to your domain",
  "longMessage": "The provided redirect URL must belong to your instance's domain",
  "code": "redirect_url_domain_mismatch"
}
```

### <code><wbr />Redirect<wbr />U<wbr />R<wbr />L<wbr />Mismatch</code>

`RedirectURLMismatch` signifies an error when the RedirectURL that was passed during an OAuth flow is not included in the redirect\_urls whitelist for that instance.

filename: Status Code: 400
```json
{
  "shortMessage": "Redirect url mismatch",
  "longMessage": "The current redirect url passed in the sign in or sign up request does not match an authorized redirect URI for this instance. Review authorized redirect urls for your instance. <val>",
  "code": "resource_missmatch"
}
```

## Requests

### <code><wbr />Invalid<wbr />Query<wbr />Parameter<wbr />Value</code>

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "<value> does not match one of the allowed values for parameter <param>",
  "code": "invalid_query_parameter_value"
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

### <code><wbr />Origin<wbr />Header<wbr />Missing</code>

`OriginHeaderMissing`

filename: Status Code: 400
```json
{
  "shortMessage": "Origin header missing",
  "longMessage": "This request requires an Origin header to be set, but it is missing",
  "code": "origin_missing"
}
```

### <code><wbr />Proxy<wbr />Request<wbr />Invalid<wbr />Secret<wbr />Key</code>

filename: Status Code: 401
```json
{
  "shortMessage": "invalid secret key",
  "longMessage": "The secret key given with this proxy request is invalid.",
  "code": "proxy_request_invalid_secret_key"
}
```

### <code><wbr />Proxy<wbr />Request<wbr />Missing<wbr />Secret<wbr />Key</code>

filename: Status Code: 400
```json
{
  "shortMessage": "missing secret key",
  "longMessage": "When using a proxy, it's required to also pass the instance secret key in the Clerk-Secret-Key header.",
  "code": "proxy_request_missing_secret_key"
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

### <code><wbr />S<wbr />A<wbr />M<wbr />L<wbr />Connection<wbr />Active<wbr />Not<wbr />Found</code>

filename: Status Code: 404
```json
{
  "shortMessage": "not found",
  "longMessage": "No active SAML Connection found with id <connectionID>.",
  "code": "saml_connection_active_not_found"
}
```

### <code><wbr />S<wbr />A<wbr />M<wbr />L<wbr />Email<wbr />Address<wbr />Domain<wbr />Mismatch</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Email address domain mismatch",
  "longMessage": "The email address domain of the provider's account does not match the domain of the connection.",
  "code": "saml_email_address_domain_mismatch",
  "meta": {
    "expecteddomain": "expecteddomain",
    "receiveddomain": "receiveddomain"
  }
}
```

### <code><wbr />S<wbr />A<wbr />M<wbr />L<wbr />Email<wbr />Address<wbr />Domain<wbr />Reserved</code>

filename: Status Code: 422
```json
{
  "shortMessage": "email address domain is used for SAML SSO",
  "longMessage": "You can't use this email address, as SAML SSO is enabled for the specific domain.",
  "code": "saml_email_address_domain_reserved"
}
```

### <code><wbr />S<wbr />A<wbr />M<wbr />L<wbr />Email<wbr />Address<wbr />Mismatch<wbr />With<wbr />Email</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Email address mismatch",
  "longMessage": "The provided email address differs from the one in the SAML response (IdP email: <email>).",
  "code": "saml_email_address_domain_mismatch"
}
```

### <code><wbr />S<wbr />A<wbr />M<wbr />L<wbr />Not<wbr />Enabled</code>

filename: Status Code: 422
```json
{
  "shortMessage": "SAML SSO not enabled",
  "longMessage": "SAML SSO is not enabled for this email address.",
  "code": "saml_connection_not_found",
  "meta": {
    "name": "param"
  }
}
```

### <code><wbr />S<wbr />A<wbr />M<wbr />L<wbr />Response<wbr />Invalid</code>

filename: Status Code: 401
```json
{
  "shortMessage": "Invalid SAML response",
  "longMessage": "The SAML response is invalid.<optionalReason>",
  "code": "saml_response_invalid"
}
```

### <code><wbr />S<wbr />A<wbr />M<wbr />L<wbr />Response<wbr />Relay<wbr />State<wbr />Missing</code>

filename: Status Code: 400
```json
{
  "shortMessage": "RelayState parameter is missing from the SAML Response",
  "longMessage": "The RelayState parameter is missing from the SAML Response. Note that RelayState is not required if you are using the IdP-initiated flow. See https://clerk.com/docs/guides/configure/auth-strategies/enterprise-connections/authentication-flows#saml",
  "code": "saml_response_relaystate_missing"
}
```

### <code><wbr />S<wbr />A<wbr />M<wbr />L<wbr />User<wbr />Attribute<wbr />Missing</code>

filename: Status Code: 400
```json
{
  "shortMessage": "",
  "longMessage": "This account does not have an associated '<attrName>' attribute. Contact the IdP administrator for resolution.",
  "code": "saml_user_attribute_missing",
  "meta": {
    "missingattribute": "attrname"
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

### <code><wbr />Invalid<wbr />Action<wbr />For<wbr />Session</code>

`InvalidActionForSession` signifies an error occurred when user tries to perform invalid action on a session

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid action for user session",
  "longMessage": "Unable to <action> session <sessionID>",
  "code": "invalid_action_for_session"
}
```

### <code><wbr />Invalid<wbr />Action<wbr />For<wbr />Session<wbr />Reverification</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid action for session reverification",
  "longMessage": "We were unable to <action> for this session, as it's not ready for <resolution>.",
  "code": "invalid_action_for_session_reverification"
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

### <code><wbr />Session<wbr />Reverification<wbr />Missing</code>

filename: Status Code: 400
```json
{
  "shortMessage": "is missing",
  "longMessage": "You need to start a new session verification flow first",
  "code": "session_reverification_missing"
}
```

### <code><wbr />Session<wbr />Reverification<wbr />Required</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Reverification required",
  "longMessage": "You need to provide additional verification to perform this operation",
  "code": "session_reverification_required"
}
```

### <code><wbr />Unauthorized<wbr />Action<wbr />For<wbr />Session</code>

`UnauthorizedActionForSession` signifies an error occurred when the requestor is not authorized to perform the
requested action to the respective session.

filename: Status Code: 401
```json
{
  "shortMessage": "Unauthorized action for session",
  "longMessage": "Not authorized to perform requested action on session <sessionID>",
  "code": "action_for_session_not_authorized"
}
```

## Sign In

### <code><wbr />Account<wbr />Lockout<wbr />Warning</code>

`AccountLockoutWarning` returns an error that warns the user about remaining attempts
before their account gets locked. This should be used when a user has 2, 1, or 0 attempts remaining.

filename: Status Code: 422
```json
{
  "shortMessage": "",
  "code": "account_lockout_warning"
}
```

### <code><wbr />Account<wbr />Transfer<wbr />Invalid</code>

`AccountTransferInvalid` signifies an error when no account was found to transfer

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid account transfer",
  "longMessage": "There is no account to transfer",
  "code": "account_transfer_invalid"
}
```

### <code><wbr />Already<wbr />Signed<wbr />In</code>

`AlreadySignedIn` signifies an error when given session ID is already signed in

filename: Status Code: 400
```json
{
  "shortMessage": "You're already signed in",
  "longMessage": "You're already signed in",
  "code": "identifier_already_signed_in",
  "meta": "session"
}
```

### <code><wbr />Identification<wbr />Belongs<wbr />To<wbr />Different<wbr />User</code>

`IdentificationBelongsToDifferentUser` indicates an error when a user
is trying to perform an operation (e.g. sign in prepare) with an
identification that doesn't belong to him.

filename: Status Code: 403
```json
{
  "shortMessage": "belongs to different user",
  "longMessage": "The given identification belongs to a different user.",
  "code": "resource_forbidden"
}
```

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

### <code><wbr />Invalid<wbr />Client<wbr />State<wbr />For<wbr />Action</code>

`InvalidClientStateForAction` signifies an error when trying to perform an invalid action for the current client state

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid action",
  "longMessage": "We were unable to complete <action> for this Client. <resolution>",
  "code": "client_state_invalid"
}
```

### <code><wbr />Invalid<wbr />Strategy<wbr />For<wbr />User</code>

`InvalidStrategyForUser` signifies an error when the supplied verification strategy is not valid for the account

filename: Status Code: 400
```json
{
  "shortMessage": "Invalid verification strategy",
  "longMessage": "The verification strategy is not valid for this account",
  "code": "strategy_for_user_invalid"
}
```

### <code><wbr />Mutation<wbr />On<wbr />Older<wbr />Sign<wbr />In<wbr />Not<wbr />Allowed</code>

`MutationOnOlderSignInNotAllowed` signifies an error when trying to mutate an older sign in

filename: Status Code: 403
```json
{
  "shortMessage": "Update operations are not allowed on older sign ins",
  "longMessage": "Update operations are not allowed on older sign ins",
  "code": "resource_forbidden"
}
```

### <code><wbr />No<wbr />Second<wbr />Factors<wbr />For<wbr />Strategy</code>

filename: Status Code: 400
```json
{
  "shortMessage": "no second factors",
  "longMessage": "No second factors were found for strategy <strategy>.",
  "code": "no_second_factors"
}
```

### <code><wbr />Sign<wbr />In<wbr />Email<wbr />Link<wbr />Not<wbr />Same<wbr />Client</code>

filename: Status Code: 403
```json
{
  "shortMessage": "email link sign in cannot be completed",
  "longMessage": "Email link sign in cannot be completed because it originates from a different client",
  "code": "sign_in_email_link_not_same_client"
}
```

### <code><wbr />Sign<wbr />In<wbr />Identification<wbr />Or<wbr />User<wbr />Deleted</code>

filename: Status Code: 400
```json
{
  "shortMessage": "identification or user deleted",
  "longMessage": "Either the user or the selected identification were deleted. Please start over.",
  "code": "sign_in_identification_or_user_deleted"
}
```

### <code><wbr />Sign<wbr />In<wbr />No<wbr />Identification<wbr />For<wbr />User</code>

filename: Status Code: 404
```json
{
  "shortMessage": "no identification for user",
  "longMessage": "The given token doesn't have an associated identification for the user who created it.",
  "code": "sign_in_no_identification_for_user"
}
```

### <code><wbr />Sign<wbr />In<wbr />Not<wbr />Found</code>

UserNotFound signifies an error when no user is found with userID

filename: Status Code: 404
```json
{
  "shortMessage": "not found",
  "longMessage": "No sign in was found with id <signInID>",
  "code": "resource_not_found"
}
```

### <code><wbr />Sign<wbr />Up<wbr />If<wbr />Missing<wbr />Identifier<wbr />Not<wbr />Supported</code>

`SignUpIfMissingIdentifierNotSupported` signifies that the identifier attribute cannot be used with sign\_up\_if\_missing

filename: Status Code: 422
```json
{
  "shortMessage": "identifier not supported with sign_up_if_missing",
  "longMessage": "The <identifier> identifier cannot be used with sign_up_if_missing, because verification is required.",
  "code": "sign_up_if_missing_not_allowed"
}
```

### <code><wbr />Sign<wbr />Up<wbr />If<wbr />Missing<wbr />Not<wbr />Allowed</code>

`SignUpIfMissingNotAllowed` signifies an error when sign\_up\_if\_missing cannot be used
due to instance configuration (restricted mode, captcha, etc.)

filename: Status Code: 422
```json
{
  "shortMessage": "sign_up_if_missing not allowed",
  "longMessage": "The sign_up_if_missing option cannot be used: <reason>",
  "code": "sign_up_if_missing_not_allowed"
}
```

### <code><wbr />Sign<wbr />Up<wbr />If<wbr />Missing<wbr />Strategy<wbr />Mismatch</code>

`SignUpIfMissingStrategyMismatch` signifies that the prepare strategy doesn't match the initial identification type

filename: Status Code: 422
```json
{
  "shortMessage": "strategy mismatch with sign_up_if_missing",
  "longMessage": "When using sign_up_if_missing, you must use a strategy that matches your initial identification type (<identificationType>), but <strategy> was provided.",
  "code": "sign_up_if_missing_strategy_not_supported"
}
```

### <code><wbr />Sign<wbr />Up<wbr />If<wbr />Missing<wbr />Strategy<wbr />Not<wbr />Supported</code>

`SignUpIfMissingStrategyNotSupported` signifies that the strategy cannot be used with sign\_up\_if\_missing

filename: Status Code: 422
```json
{
  "shortMessage": "strategy not supported with sign_up_if_missing",
  "longMessage": "The <strategy> strategy cannot be used with the sign_up_if_missing option because it cannot be used to sign up a new user.",
  "code": "sign_up_if_missing_strategy_not_supported"
}
```

### <code><wbr />Sign<wbr />Up<wbr />If<wbr />Missing<wbr />Transfer</code>

filename: Status Code: 404
```json
{
  "shortMessage": "user not found, transfer to sign up",
  "longMessage": "The sign in failed because there is no matching user. Please perform a transfer to sign up.",
  "code": "sign_up_if_missing_transfer"
}
```

### <code><wbr />Single<wbr />Mode<wbr />Session<wbr />Exists</code>

`SingleModeSessionExists` signifies an error when session already exists but we are in single session mode

filename: Status Code: 400
```json
{
  "shortMessage": "Session already exists",
  "longMessage": "You're already signed in.",
  "code": "session_exists"
}
```

## Sign In Tokens

### <code><wbr />Sign<wbr />In<wbr />Token<wbr />Already<wbr />Used</code>

filename: Status Code: 400
```json
{
  "shortMessage": "sign in token has already been used",
  "longMessage": "This sign in token has already been used. Each token can only be used once.",
  "code": "sign_in_token_already_used_code"
}
```

### <code><wbr />Sign<wbr />In<wbr />Token<wbr />Can<wbr />Be<wbr />Used<wbr />Only<wbr />In<wbr />Sign<wbr />In</code>

filename: Status Code: 400
```json
{
  "shortMessage": "not in sign in",
  "longMessage": "Sign in tokens can only be used during sign in.",
  "code": "sign_in_token_not_in_sign_in_code"
}
```

### <code><wbr />Sign<wbr />In<wbr />Token<wbr />Cannot<wbr />Be<wbr />Used</code>

filename: Status Code: 400
```json
{
  "shortMessage": "sign in token cannot be used",
  "longMessage": "This sign in token cannot be used anymore. Please request a new one.",
  "code": "sign_in_token_cannot_be_used_code"
}
```

### <code><wbr />Sign<wbr />In<wbr />Token<wbr />Revoked</code>

filename: Status Code: 400
```json
{
  "shortMessage": "sign in token has been revoked",
  "longMessage": "This sign in token has been revoked and cannot be used anymore.",
  "code": "sign_in_token_revoked_code"
}
```

## Sign Up

### <code><wbr />Captcha<wbr />Client<wbr />Side<wbr />Error</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Error loading CAPTCHA",
  "longMessage": "The CAPTCHA failed to load. This may be due to an unsupported browser or a browser extension. Please try a different browser or disabling extensions. If this issue persists, please contact support.",
  "code": "captcha_invalid"
}
```

### <code><wbr />Captcha<wbr />Invalid</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Authentication unsuccessful due to failed security validations.",
  "longMessage": "Authentication unsuccessful due to failed security validations. Please try using a different browser or disabling browser extensions. If issues persist, contact support for assistance.",
  "code": "captcha_invalid"
}
```

### <code><wbr />Captcha<wbr />Missing<wbr />Token</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Authentication unsuccessful due to failed security validations.",
  "longMessage": "Authentication unsuccessful due to failed security validations. Please refresh the page to try again or reach out to support for more assistance.",
  "code": "captcha_missing_token"
}
```

### <code><wbr />Captcha<wbr />Not<wbr />Enabled</code>

filename: Status Code: 400
```json
{
  "shortMessage": "CAPTCHA not enabled",
  "longMessage": "You attempted to complete a CAPTCHA, but they are not enabled. If this issue persists, please contact support.",
  "code": "captcha_not_enabled"
}
```

### <code><wbr />Sign<wbr />Up<wbr />Email<wbr />Link<wbr />Not<wbr />Same<wbr />Client</code>

filename: Status Code: 403
```json
{
  "shortMessage": "email link sign up cannot be completed",
  "longMessage": "Email link sign up cannot be completed because it originates from a different client",
  "code": "sign_up_email_link_not_same_client"
}
```

### <code><wbr />Sign<wbr />Up<wbr />Forbidden<wbr />Access</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Sign up forbidden",
  "longMessage": "Access to this sign up is forbidden",
  "code": "resource_forbidden"
}
```

### <code><wbr />Sign<wbr />Up<wbr />Mode<wbr />Restricted</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Sign-ups restricted",
  "longMessage": "New sign-ups are currently restricted.",
  "code": "sign_up_mode_restricted"
}
```

### <code><wbr />Sign<wbr />Up<wbr />Mode<wbr />Restricted<wbr />Waitlist</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Sign-ups restricted with waitlist",
  "longMessage": "Sign-ups are currently unavailable. Join the waitlist, and you will be notified when access becomes available.",
  "code": "sign_up_restricted_waitlist"
}
```

### <code><wbr />Sign<wbr />Up<wbr />Not<wbr />Found</code>

`SignUpNotFound` returns an API error where no sign up could be found with
the requested ID.

filename: Status Code: 404
```json
{
  "shortMessage": "Sign up not found",
  "longMessage": "No sign up was found with id <id>",
  "code": "resource_not_found"
}
```

## Sms

### <code><wbr />Dev<wbr />Monthly<wbr />S<wbr />M<wbr />S<wbr />Limit<wbr />Exceeded</code>

`DevMonthlySMSLimitExceeded` signifies an error when an SMS sending attempt is made while the development limit has already been reached

filename: Status Code: 400
```json
{
  "shortMessage": "Development monthly SMS limit exceeded",
  "longMessage": "Operation cannot be completed because the monthly limit for SMS messages in development (%d) has been reached.",
  "code": "dev_monthly_sms_limit_exceeded",
  "meta": "{\"limit\"}"
}
```

### <code><wbr />S<wbr />M<wbr />S<wbr />Send<wbr />Error</code>

filename: Status Code: 400
```json
{
  "shortMessage": "Sending SMS failed",
  "longMessage": "Sending SMS failed. Please contact support or try again later.",
  "code": "sms_send_error"
}
```

## Ticket

### <code><wbr />Ticket<wbr />Expired</code>

filename: Status Code: 400
```json
{
  "shortMessage": "ticket has expired",
  "longMessage": "This ticket has expired and cannot be used anymore.",
  "code": "ticket_expired_code"
}
```

### <code><wbr />Ticket<wbr />Invalid</code>

filename: Status Code: 400
```json
{
  "shortMessage": "ticket is invalid",
  "longMessage": "This ticket is invalid. Make sure you're using a valid ticket generated by Clerk.",
  "code": "ticket_invalid_code"
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

### <code><wbr />T<wbr />O<wbr />T<wbr />P<wbr />Already<wbr />Enabled</code>

`TOTPAlreadyEnabled` signifies an error when a user attempts to enable TOTP, but it's already enabled.

filename: Status Code: 400
```json
{
  "shortMessage": "TOTP already enabled",
  "longMessage": "TOTP is already enabled on your account",
  "code": "totp_already_enabled"
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

### <code><wbr />Invalid<wbr />U<wbr />R<wbr />L<wbr />Scheme</code>

filename: Status Code: 422
```json
{
  "shortMessage": "Invalid URL scheme",
  "longMessage": "Please provide a URL with one of the following schemes: <schemes>",
  "code": "invalid_url_scheme",
  "meta": {
    "name": "paramname"
  }
}
```

## User Lockout

### <code><wbr />User<wbr />Locked</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Account locked",
  "longMessage": "Your account is locked. You will be able to try again in <timeRemaining>. For more information, please contact <support>.",
  "code": "user_locked"
}
```

### <code><wbr />User<wbr />Locked<wbr />Indefinitely</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Account locked",
  "longMessage": "Your account is locked. For more information, please contact <support>.",
  "code": "user_locked"
}
```

## User Settings

### <code><wbr />Resource<wbr />Forbidden</code>

filename: Status Code: 403
```json
{
  "shortMessage": "forbidden",
  "longMessage": "Resource forbidden",
  "code": "resource_forbidden"
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

### <code><wbr />No<wbr />Password<wbr />Set</code>

filename: Status Code: 400
```json
{
  "shortMessage": "no password set",
  "longMessage": "This user does not have a password set for their account",
  "code": "no_password_set"
}
```

### <code><wbr />Password<wbr />Required</code>

filename: Status Code: 400
```json
{
  "shortMessage": "password required",
  "longMessage": "Settings for this instance require a password to be set. Cannot remove the user's password.",
  "code": "password_required"
}
```

### <code><wbr />Password<wbr />Too<wbr />Long<wbr />Needs<wbr />Reset</code>

filename: Status Code: 422
```json
{
  "shortMessage": "imported password too long and needs reset",
  "longMessage": "The existing imported password is too long and cannot be used, please reset your password.",
  "code": "password_too_long_needs_reset"
}
```

### <code><wbr />Updating<wbr />User<wbr />Password<wbr />Deprecated</code>

filename: Status Code: 403
```json
{
  "shortMessage": "deprecated feature",
  "longMessage": "Password is not a valid parameter and can only be updated via /v1/me/change_password",
  "code": "updating_user_password_deprecated"
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

### <code><wbr />User<wbr />Create<wbr />Org<wbr />Not<wbr />Enabled</code>

filename: Status Code: 403
```json
{
  "shortMessage": "create organization not enabled",
  "longMessage": "Organization creation is not enabled for this user",
  "code": "user_create_organization_not_enabled"
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

### <code><wbr />User<wbr />Delete<wbr />Self<wbr />Not<wbr />Enabled</code>

filename: Status Code: 403
```json
{
  "shortMessage": "delete self not enabled",
  "longMessage": "Self deletion is not enabled for this user",
  "code": "user_delete_self_not_enabled"
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

## Verification

### <code><wbr />Verification<wbr />Already<wbr />Verified</code>

`VerificationAlreadyVerified` signifies an error when verification has already been verified

filename: Status Code: 400
```json
{
  "shortMessage": "already verified",
  "longMessage": "This verification has already been verified.",
  "code": "verification_already_verified"
}
```

### <code><wbr />Verification<wbr />Code<wbr />Too<wbr />Many<wbr />Requests</code>

filename: Status Code: 429
```json
{
  "shortMessage": "Too many verification code requests",
  "longMessage": "Too many verification code requests. Please wait at least 30 seconds to receive your code before trying again.",
  "code": "verification_code_too_many_requests"
}
```

### <code><wbr />Verification<wbr />Expired</code>

`VerificationExpired` signifies an error when verification has expired

filename: Status Code: 400
```json
{
  "shortMessage": "expired",
  "longMessage": "This verification has expired. You must create a new one.",
  "code": "verification_expired"
}
```

### <code><wbr />Verification<wbr />Failed</code>

`VerificationFailed` signifies an error when verification fails

filename: Status Code: 400
```json
{
  "shortMessage": "failed",
  "longMessage": "Too many failed attempts. You have to try again with the same or another method.",
  "code": "verification_failed"
}
```

### <code><wbr />Verification<wbr />Invalid<wbr />Link<wbr />Token</code>

`VerificationInvalidLinkToken` means that the provided JWT token from the
link cannot be parsed.

filename: Status Code: 400
```json
{
  "shortMessage": "invalid link token",
  "longMessage": "Verification link token is invalid",
  "code": "verification_link_token_invalid"
}
```

### <code><wbr />Verification<wbr />Invalid<wbr />Link<wbr />Token<wbr />Source</code>

`VerificationInvalidLinkTokenSource` means that the provided JWT token from
the link has an invalid source type.

filename: Status Code: 400
```json
{
  "shortMessage": "invalid link token source",
  "longMessage": "Verification link token source is invalid",
  "code": "verification_link_token_source_invalid"
}
```

### <code><wbr />Verification<wbr />Invalid<wbr />Strategy</code>

`VerificationInvalidStrategy` signifies an error when the given strategy is not valid for current verification

filename: Status Code: 400
```json
{
  "shortMessage": "has invalid strategy",
  "longMessage": "The strategy is not valid for the current verification.",
  "code": "verification_strategy_invalid"
}
```

### <code><wbr />Verification<wbr />Link<wbr />Token<wbr />Expired</code>

`VerificationLinkTokenExpired` means that the provided JWT token from the
link has expired.

filename: Status Code: 400
```json
{
  "shortMessage": "expired link token",
  "longMessage": "Verification link token has expired",
  "code": "verification_link_token_expired"
}
```

### <code><wbr />Verification<wbr />Link<wbr />Token<wbr />Stale</code>

`VerificationLinkTokenStale` means that the verification link token references
a verification that is no longer current (e.g. the user requested a new
verification after this link was sent).

filename: Status Code: 400
```json
{
  "shortMessage": "stale link token",
  "longMessage": "Verification link token is no longer valid. Please request a new one.",
  "code": "verification_link_token_stale"
}
```

### <code><wbr />Verification<wbr />Missing</code>

`VerificationMissing` signifies an error when the verification is missing

filename: Status Code: 400
```json
{
  "shortMessage": "is missing",
  "longMessage": "This strategy requires verification preparation before attempting to validate it.",
  "code": "verification_missing"
}
```

### <code><wbr />Verification<wbr />Not<wbr />Sent</code>

`VerificationNotSent` signifies an error when verification email was not sent

filename: Status Code: 400
```json
{
  "shortMessage": "not sent",
  "longMessage": "You need to send a verification code before attempting to verify.",
  "code": "verification_not_sent"
}
```

### <code><wbr />Verification<wbr />Unknown<wbr />Status</code>

`VerificationUnknownStatus` signifies an unexpected error when unknown verification status is found

filename: Status Code: 500
```json
{
  "shortMessage": "Unknown verification status",
  "longMessage": "Found unknown verification status <status>",
  "code": "verification_status_unknown"
}
```

## Waitlist

### <code><wbr />Waitlist<wbr />Not<wbr />Accepting<wbr />Entries</code>

filename: Status Code: 403
```json
{
  "shortMessage": "Waitlist not accepting entries",
  "longMessage": "The waitlist is not accepting new entries at this time. Please try again later.",
  "code": "waitlist_not_accepting_entries"
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
