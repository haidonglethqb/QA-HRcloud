# Integrations Module

**Support URL**: https://support.hrcloud.com/en/help-center/integrations  
**Total Articles**: 56  
**App URL**: `/settings/integrations`

---

## Overview

HRcloud integrates with **56+ third-party platforms** for payroll, HRIS sync, background checks, calendars, SSO, and more.

### Integration Categories

| Category | Examples |
|----------|---------|
| **Payroll** | ADP, Paychex, Gusto, QuickBooks Payroll, Paycom, UKG, Paylocity, Rippling, TriNet |
| **Benefits** | PlanSource, Maxwell Health |
| **Background Checks** | Checkr, Verified First |
| **SSO / Identity** | Azure AD, Okta, Google Workspace, JumpCloud |
| **Calendar** | Google Calendar, Microsoft Outlook / Office 365 |
| **ATS / Recruit** | JazzHR, Greenhouse, Lever, Workday, BambooHR |
| **Communication** | Slack, Teams, Zoom |
| **Learning** | Lessonly, 360Learning |
| **Other** | PandaDoc, DocuSign, Zapier, BambooHR |

---

## Navigation Paths

| Action | Navigation |
|--------|-----------|
| Integrations Page | Settings -> "Integrations" OR `/settings/integrations` |
| Connect an Integration | Integrations -> Find integration -> "Connect" / "Setup" button |
| Manage Active Integration | Integrations -> Click connected integration card |
| Disconnect Integration | Integration settings -> "Disconnect" or "Disable" |

---

## Key Integration Types & Business Rules

### Payroll Integrations (ADP, Paychex, Gusto, etc.)
**Data Sync Direction**: HRcloud -> Payroll
- New employees sync when created in HRcloud
- Employment changes (department, position, salary) sync to payroll
- Terminations sync to payroll
- Time Off and Time Clock data sync for payroll calculation
- **Important**: Employees must be **matched** between systems (by SSN, EIN, or employee ID)
- **One-way sync** by default - payroll is the source of truth for compensation

### ADP Specifically
- Multiple ADP products supported: ADP Workforce Now, ADP Run
- Setup requires: integration credentials from ADP and company code
- Sync schedule: real-time (event-based) or scheduled (nightly)
- **Fields synced**: name, SSN, hire date, employment type, department, position, location, termination

### Background Check Integrations (Checkr, Verified First)
- Trigger background check from Recruit module (applicant profile)
- Results appear in applicant record
- Status updates automatically (pending -> clear -> consider)
- Requires account with background check provider

### Calendar Integrations (Google, Outlook)
- Time off events sync to personal calendar
- Interview events from Recruit sync to calendar
- Requires employee to authorize their calendar

### SSO Integrations
- See `user_management.md` for SSO details
- SAML 2.0 support for: Azure AD, Okta, Google Workspace, JumpCloud
- After SSO is configured, users log in via SSO provider

### Slack / Teams Integration
- Notifications sent to Slack/Teams channels
- Kudos announcements, new hire announcements, time off approvals
- Workmates posts can cross-post to Slack

### Zapier
- No-code automation: trigger HRcloud events -> actions in other apps
- Use cases: Google Sheets, Airtable, Mailchimp

---

## Common Integration Issues

| Issue | Solution |
|-------|---------|
| Employee not syncing to payroll | Check if employee is "matched" in integration settings |
| Sync delay | Check integration logs in Settings -> Integrations -> [provider] -> Logs |
| Auth errors | Re-authenticate / reconnect the integration in settings |
| Field mismatch | Map fields correctly in integration setup wizard |

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).

