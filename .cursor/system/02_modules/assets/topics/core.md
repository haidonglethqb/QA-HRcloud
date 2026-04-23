# Assets Module

**Support URL**: https://support.hrcloud.com/en/help-center/assets  
**Total Articles**: 6  
**App URL**: `/assets`

---

## Overview

The Assets module tracks **company-owned equipment and items** assigned to employees - laptops, phones, access cards, vehicles, and more.

### Key Capabilities
- Create and manage asset records
- Assign assets to employees
- Track asset status (available, assigned, lost, returned)
- Asset checkout and return workflows
- Custom asset fields and categories
- Reports and exports

---

## Navigation Paths

| Action | Navigation |
|--------|-----------|
| Assets Home | Sidebar -> Assets OR `/assets` |
| Asset List | Assets -> "All Assets" |
| Add New Asset | Assets -> "Add Asset" button |
| Assign Asset | Assets -> Click asset -> "Assign" button |
| Return Asset | Assets -> Click asset -> "Return" |
| Asset Settings | Settings -> Assets |

---

## Key Features & Business Rules

### Asset Types / Categories
- Admin creates asset categories: Electronics, Furniture, Vehicles, Access Cards, etc.
- Each asset has: name, serial number, category, condition, purchase date, assigned employee

### Asset States
- **Available**: Not assigned to anyone
- **Assigned**: Currently with an employee
- **Returned**: Previously assigned, now returned
- **Lost/Stolen**: Marked as lost
- **Retired/Disposed**: No longer in service

### Assignment Flow
1. Admin creates asset record
2. Assigns asset to employee (along with date and notes)
3. Employee can see assigned assets on their profile
4. When asset is returned: admin marks it as "Returned"

### Integration with Onboard/Offboard
- Onboard checklist task: "Assign laptop" -> triggers asset assignment
- Offboard checklist task: "Return all assets" -> tracks asset return

### Custom Fields
- Admin can add custom fields to asset records
- Example: invoice number, purchase price, warranty expiry

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).

