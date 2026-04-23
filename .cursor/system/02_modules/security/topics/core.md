# Security Module

**Support URL**: https://support.hrcloud.com/en/help-center/security  
**Total Articles**: 1  
**App URL**: `/settings/security`

---

## Overview

The Security module covers HRcloud's **platform security settings** - access controls, privacy rules, data retention, and audit logs.

### Key Settings
- Two-Factor Authentication (2FA) enforcement
- SSO configuration
- Password policy
- Session timeout settings
- IP allowlisting (restrict access to specific IPs)
- Activity log / audit trail
- Data retention and GDPR compliance rules

---

## Navigation Paths

| Action | Navigation |
|--------|-----------|
| Security Settings | Settings -> "Security" section |
| 2FA Configuration | Settings -> Security -> "Two-Factor Authentication" |
| SSO Setup | Settings -> Security -> "Single Sign-On" |
| Password Policy | Settings -> Security -> "Password Policy" |
| Activity Log | Settings -> Security -> "Activity Log" |
| IP Allowlist | Settings -> Security -> "IP Restrictions" |

---

## Key Business Rules

### 2FA
- Can be enforced: for all users, only admins, or optional per user
- Methods: TOTP (Google Authenticator, Authy), SMS
- If 2FA is enforced, users must set it up on their next login

### Password Policy
- minimum length (8+ characters recommended)
- Complexity: uppercase, lowercase, number, special character
- Expiry: force password change every X days
- No reuse of last N passwords

### Session Management
- Auto-logout after idle period (configurable)
- Active sessions can be viewed and terminated by admin

### Activity Log
- Tracks: logins, setting changes, bulk operations, role changes
- Per-user and system-wide views
- Can be filtered by date, user, action type
- Export to CSV

### IP Restrictions
- Allow login only from specific IP ranges
- Useful for corporate VPN requirements

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).

