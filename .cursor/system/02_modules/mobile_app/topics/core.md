# Mobile App Module

**Support URL**: https://support.hrcloud.com/en/help-center/mobile-app  
**Total Articles**: 4  
**App URL**: Native iOS / Android App

---

## Overview

HRcloud has a **native mobile app** (iOS and Android) providing employees with access to key features on the go.

### Available on Mobile
- Workmates feed (view, post, comment, react)
- Kudos (give and receive)
- Time Off requests (submit and approve)
- Time Clock (clock in/out via phone GPS)
- Profile (view and edit personal info)
- Notifications (push notifications)
- Chat (messaging)
- Tasks (complete onboarding tasks)

### NOT Available on Mobile
- Full admin settings
- Complex configuration (checklists setup, roles, etc.)
- Some advanced reporting

---

## Navigation Paths on Mobile

| Action | Method |
|--------|--------|
| Download App | App Store (iOS) / Google Play (Android) |
| Login | Email + Password OR SSO |
| Switch modules | Bottom tab bar OR hamburger menu |
| View Workmates feed | Workmates tab |
| Request Time Off | Time Off tab -> "+ Request" |
| Clock In | Time Clock tab -> "Clock In" |
| View Profile | Profile tab (usually bottom right) |

---

## Key Business Rules (Mobile)

### Geofencing for Time Clock
- If geofencing is configured by admin, employees can only clock in when within the allowed location radius
- GPS permission must be granted to the app

### Push Notifications
- Employees receive push notifications for: task assignments, time off decisions, mentions, Kudos received
- Notifications can be customized in app settings

### Offline Mode
- Limited offline support - primary functions require internet connection
- Feed may cache recent posts for quick loading

### Mobile-specific Settings
- Admin can control mobile app availability per employee group
- Some features may be disabled for specific organizations

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).

