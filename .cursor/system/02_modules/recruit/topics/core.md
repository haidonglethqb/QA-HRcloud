# Recruit Module

**Support URL**: https://support.hrcloud.com/en/help-center/recruit  
**Total Articles**: 32  
**App URL**: `/recruit`

---

## Overview

The Recruit module is HRcloud's **Applicant Tracking System (ATS)**. It manages job postings, applicant pipelines, interviews, and the transition from applicant -> new hire.

### Key Capabilities
- Job posting creation and management
- Public-facing Job Board (customizable)
- Applicant pipeline (Kanban or list view by status)
- Application form customization
- Interview scheduling with calendar integration
- Offer letter creation and e-signature
- Email and SMS templates for applicant communication
- Integration with third-party ATSs (JazzHR, Greenhouse, Lever, and others)
- Background check integrations (Checkr, Verified First)
- Data retention policies (GDPR compliance)
- Reports and analytics

---

## Navigation Paths

| Action | Navigation |
|--------|-----------|
| Recruit Dashboard | Sidebar -> Recruit OR `/recruit` |
| Jobs List | Recruit -> "Jobs" tab |
| Create New Job | Recruit -> Jobs -> "Create Job" button |
| Applicant List | Recruit -> "Applicants" tab |
| Specific Applicant | Recruit -> Applicants -> Click applicant name |
| Job Board (admin view) | Recruit -> "Job Board" |
| Reports | Recruit -> "Reports" tab |
| Recruit Settings | Settings -> Recruit |

---

## Topic Files

- [jobs and pipeline](./jobs_and_pipeline.md): access model, jobs, job boards, and applicant status behavior.
- [hiring and communication](./hiring_and_communication.md): offer letters, hiring conversion, communications, interviews, privacy, retention, and ratings.

## Test-Critical Rules

- Only users with Recruit access can see the module.
- Jobs must be `Published` before they appear on the job board.
- Applicant statuses are configurable and can be reordered.
- Hiring can happen with or without an offer letter.
- Hiring a previously terminated employee must use the rehire flow.
- Privacy, retention, and rating behavior affect recruiter-visible outcomes.

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).

