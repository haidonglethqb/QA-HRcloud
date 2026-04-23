# Advanced / Forms Module

**Support URL**: https://support.hrcloud.com/en/help-center/advanced  
**Total Articles**: 18  
**App URL**: `/settings/forms` and various advanced features

---

## Overview

The "Advanced" category covers **advanced platform features** that cut across multiple modules - primarily form building, e-signatures, and complex automation.

### Key Capabilities
- PDF form uploads with fillable field mapping
- E-Form builder (from scratch)
- E-signature workflows (single and counter-signature)
- Form embed on external websites
- Form share via public link
- Merge fields (auto-populate from employee data)
- Document request tasks
- Custom file naming conventions
- Form versioning

---

## Navigation Paths

| Action | Navigation |
|--------|-----------|
| Forms List | Settings -> "Forms" tab |
| Upload New Form | Settings -> Forms -> "Add Form" / "Upload" |
| Edit Existing Form | Settings -> Forms -> Click form name |
| Form Preview | Settings -> Forms -> Click form -> "Preview" |
| Share Form Link | Settings -> Forms -> Click form -> "Share Link" |
| Embed Form | Settings -> Forms -> Click form -> "Embed" |

---

## Key Features & Business Rules

### Form Types
1. **PDF Upload**: Upload existing PDF -> add fillable fields, signature fields, merge fields
2. **E-Form Builder**: Build form from scratch with drag-and-drop fields
3. **Document Request**: Not a form per se - employee uploads a file

### Fillable Fields
- Text, date, number, checkbox, dropdown, signature
- Each field linked to a form section
- **Required vs. optional** per field
- **Conditional fields**: show/hide based on other field responses (advanced feature)

### Merge Fields
- Auto-populate fields with employee data from their profile
- Examples: `{{firstName}}`, `{{lastName}}`, `{{startDate}}`, `{{position}}`
- List of available merge fields is shown in form editor

### E-Signature Fields
- Employee signs with mouse/touch draw OR typed name
- Timestamp recorded
- PDF with signature generated and stored

### Counter Signature
- After employee signs, a second party (manager/HR) must also sign
- Counter-signature initiates after employee's submission
- Both signatures appear on final document

### Form Versions
- When a form is edited, a new version is created
- Historical submissions attached to the version at time of creation
- Can roll back to previous version

### Sharing & Embedding
- **Share link**: public URL anyone can fill (used for candidates, prehires)
- **Embed**: embed form in company website/intranet via iframe code

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).

