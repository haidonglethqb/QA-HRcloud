# HR Cloud Settings Module

**Support URL**: https://support.hrcloud.com/en/help-center/hr-cloud-settings  
**Total Articles**: 35  
**App URL**: `/settings`

---

## Overview

HR Cloud Settings is the **central administration hub** where admins configure company-wide settings, policies, integrations, and system behavior.

### Key Capabilities
- Company information and branding
- Positions, Departments, Divisions, Locations management
- Employment types and status configurations
- Working time policies
- Email alerts and notifications
- Data import/export tools
- Employee lookup fields customization
- Custom fields for employee profiles
- Calendar settings
- AI feature settings
- Forms management (e-forms, document templates)
- Payroll configuration

---

## Navigation Paths

| Action | Navigation |
|--------|-----------|
| Settings Home | Sidebar -> gear icon OR `/settings` |
| Company Info | Settings -> "Company" tab |
| Positions | Settings -> Company -> "Positions" |
| Departments | Settings -> Company -> "Departments" |
| Divisions | Settings -> Company -> "Divisions" |
| Locations | Settings -> Company -> "Locations" |
| Employment Types | Settings -> Company -> "Employment Types" |
| Working Time Policy | Settings -> "Working Time Policy" |
| Email Alerts | Settings -> "Email Alerts" |
| Import Data | Settings -> "Import" |
| Custom Fields | Settings -> "Custom Fields" |
| Calendar | Settings -> "Calendar" |
| AI Settings | Settings -> "AI" |

---

## Topic Files

- [company structure](./company_structure.md): company profile, org structure, employment types, and status setup.
- [policies and admin tools](./policies_and_admin_tools.md): working time, calendars, alerts, imports, custom fields, forms, and AI settings.

## Test-Critical Rules

- Positions, departments, divisions, locations, and employment types feed downstream modules.
- Status types and working-time policy changes affect employee state and time calculations.
- Email alerts are configurable per module and per event.
- Import tools rely on system templates and can affect live employee data.
- Forms and AI settings change behavior outside Settings itself.

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).

