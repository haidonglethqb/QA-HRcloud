# User Management Identity and Security

Use this topic for invites, account identity rules, SSO, 2FA, and password policy behavior.

## Inviting Users

- Admin enters email and assigns role.
- User receives an email invitation.
- User sets their own password through the activation link.

## Employee vs. User

- **Employee** means a person with a People profile.
- **User** means a person with login credentials.
- These are usually the same person, but not always.
- Example: a payroll vendor may be a User without being an Employee.

## SSO Integration

- Supports SAML 2.0 based SSO.
- Can be configured with Azure AD, Google Workspace, Okta, and others.
- When SSO is enabled, password login is disabled unless admin re-enables it.

## 2FA

- 2FA can be enforced for all users or only Admins.
- Supported methods include authenticator app (TOTP) and SMS.

## Password Policy

- Minimum length and complexity rules can be configured.
- Password expiry can be enforced.
- First-login password reset can be required.
