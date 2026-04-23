# HRcloud URL Map — All Module Routes

Base URL: `https://app.hrcloud.com`

> Use these URLs for direct navigation with `page.goto()` in Playwright.

---

## Authentication

| Page | URL Path | Notes |
|------|----------|-------|
| Login | `/login` | Email + Password |
| Forgot Password | `/forgot-password` | Email reset flow |
| Activation | `/activate/:token` | Via activation email link |

---

## Dashboard

| Page | URL Path |
|------|----------|
| Main Dashboard | `/dashboard` or `/home` |

---

## Workmates & Kudos

| Page | URL Path | Notes |
|------|----------|-------|
| Workmates Home (Company Feed) | `/workmates` | Main feed |
| Workmates Chat | `/workmates/chat` | Messaging |
| Workmates Analytics | `/workmates/analytics` | Admin only |
| Channel List | `/workmates/channels` | All channels |
| Specific Channel | `/workmates/channels/:id` | |
| Kudos | `/workmates/kudos` | Give/view kudos |
| Kudos Analytics | `/workmates/kudos/analytics` | |
| Surveys | `/workmates/surveys` | |
| Pages | `/workmates/pages` | |
| Campaigns | `/workmates/campaigns` | |
| Workmates Settings | `/settings/workmates` | Admin settings |

---

## People

| Page | URL Path | Notes |
|------|----------|-------|
| People List | `/people` | Employee directory |
| Employee Profile | `/people/:employeeId` | |
| Employee Profile - Personal | `/people/:employeeId/personal` | |
| Employee Profile - Employment | `/people/:employeeId/employment` | |
| Employee Profile - Documents | `/people/:employeeId/documents` | |
| Employee Profile - Tasks | `/people/:employeeId/tasks` | |
| Employee Profile - Notes | `/people/:employeeId/notes` | |
| Org Chart | `/people/orgchart` | |
| Reports | `/people/reports` | |
| Add New Employee | `/people/new` or modal on `/people` | |
| People Settings | `/settings/people` | |

---

## Onboard

| Page | URL Path | Notes |
|------|----------|-------|
| Onboard Dashboard | `/onboard` | Overview |
| Checklists List | `/onboard/checklists` | All templates |
| Edit Checklist | `/onboard/checklists/:id` | |
| New Checklist | `/onboard/checklists/new` | |
| Employee Tasks View | `/onboard/employees/:id` | Employee-specific |
| Portals | `/onboard/portals` | Prehire portals |
| Smartflow | `/onboard/smartflow` | |
| Onboard Settings | `/settings/onboard` | |

---

## Offboard

| Page | URL Path | Notes |
|------|----------|-------|
| Offboard Dashboard | `/offboard` | |
| Offboard Checklists | `/offboard/checklists` | |
| Terminate Employee | Triggered from People module | Modal |

---

## Recruit

| Page | URL Path | Notes |
|------|----------|-------|
| Recruit Dashboard | `/recruit` | |
| Job Listings | `/recruit/jobs` | All job postings |
| Create Job | `/recruit/jobs/new` | |
| Applicant List | `/recruit/applicants` | |
| Applicant Profile | `/recruit/applicants/:id` | |
| Job Board | `/recruit/job-board` | Public-facing |
| Reports | `/recruit/reports` | |
| Recruit Settings | `/settings/recruit` | Email templates, etc. |

---

## Time Off

| Page | URL Path | Notes |
|------|----------|-------|
| Time Off Dashboard | `/timeoff` | Overview |
| My Time Off | `/timeoff/my-time-off` | Employee view |
| Time Off Requests | `/timeoff/requests` | Manager/Admin |
| Time Off Policies | `/timeoff/policies` | Admin only |
| Time Off Types | `/timeoff/types` | Admin only |
| Balance Grid | `/timeoff/balance` | Admin view |
| Calendar | `/calendar` | Shared calendar |
| Time Off Settings | `/settings/timeoff` | |

---

## Perform

| Page | URL Path | Notes |
|------|----------|-------|
| Perform Dashboard | `/perform` | |
| Performance Cycles | `/perform/cycles` | |
| Create Cycle | `/perform/cycles/new` | |
| My Reviews | `/perform/reviews` | Employee view |
| Goals | `/perform/goals` | |
| Analytics / Matrix | `/perform/analytics` | Admin/Manager |
| Perform Settings | `/settings/perform` | |

---

## Time Clock

| Page | URL Path | Notes |
|------|----------|-------|
| Time Clock Dashboard | `/timeclock` | |
| Timesheets | `/timeclock/timesheets` | Manager approval |
| Projects | `/timeclock/projects` | |
| Time Clock Settings | `/settings/timeclock` | |

---

## Assets

| Page | URL Path | Notes |
|------|----------|-------|
| Assets Dashboard | `/assets` | |
| Asset List | `/assets/list` | |
| Add Asset | `/assets/new` | |
| Asset Detail | `/assets/:id` | |
| Assets Settings | `/settings/assets` | |

---

## Shift Planner

| Page | URL Path | Notes |
|------|----------|-------|
| Shift Planner Dashboard | `/shift-planner` | |
| Schedule View | `/shift-planner/schedule` | |
| Open Shifts | `/shift-planner/open-shifts` | |
| Shift Settings | `/settings/shift-planner` | |

---

## Settings

| Page | URL Path | Notes |
|------|----------|-------|
| Settings Home | `/settings` | |
| Company Info | `/settings/company` | |
| Positions | `/settings/company/positions` | |
| Departments | `/settings/company/departments` | |
| Locations | `/settings/company/locations` | |
| Divisions | `/settings/company/divisions` | |
| Employment Types | `/settings/company/employment-types` | |
| Security / Roles | `/settings/security` | |
| Email Alerts | `/settings/email-alerts` | |
| Import Data | `/settings/import` | |
| Integrations | `/settings/integrations` | |
| Employee Groups | `/settings/employee-groups` | |
| Working Time Policy | `/settings/working-time` | |
| Calendar Settings | `/settings/calendar` | |
| AI Settings | `/settings/ai` | |
| User Management | `/settings/users` | |

---

## URL Pattern Notes

- `:employeeId` = numeric or UUID employee identifier
- `:id` = numeric or UUID record identifier  
- `:token` = activation/reset token from email
- Most list pages support query params: `?search=name&status=active&page=2`
- Settings sub-pages may use hash routing: `/settings#company`
