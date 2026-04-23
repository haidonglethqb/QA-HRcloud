# Playwright MCP — How the Agent Interacts with HRcloud

> The agent uses **Playwright MCP tools** to control the browser. Do NOT write JavaScript code.
> This file explains how to use MCP tools correctly when working with HRcloud.

---

## Core MCP Tools

| Tool | Description | When to use |
|------|-------------|-------------|
| `browser_navigate` | Open a URL | Start test, switch module |
| `browser_click` | Click an element | Button, link, dropdown, checkbox |
| `browser_type` | Type text into an input | Form fields, search box |
| `browser_select_option` | Choose option in `<select>` | Native HTML select dropdown |
| `browser_screenshot` | Capture a screenshot | Verify UI, log bug evidence |
| `browser_snapshot` | Get accessibility tree of page | Find elements, read state |
| `browser_wait_for` | Wait for element to appear/disappear | After actions, during page load |
| `browser_hover` | Hover over an element | Tooltip, hover dropdown |
| `browser_check` | Check a checkbox | Checkbox, radio button |
| `browser_press_key` | Press a keyboard key | Enter, Tab, Escape |
| `browser_scroll` | Scroll the page | Lazy-load content, reach footer |

---

## Login to HRcloud

```
1. browser_navigate → https://app.hrcloud.com/login
2. browser_snapshot → confirm login form is visible
3. browser_click    → email input field
4. browser_type     → [email address]
5. browser_click    → password input field
6. browser_type     → [password]
7. browser_click    → "Log In" / "Sign In" button
8. browser_wait_for → URL contains "/dashboard" OR dashboard element appears
9. browser_screenshot → confirm successful login
```

---

## Navigating to a Module

### Fastest method — Direct URL
```
browser_navigate  → [module URL from url_map.md]
browser_wait_for  → main element of the module appears
browser_screenshot → confirm you are on the correct page
```

> See `../01_navigation/url_map.md` for all module URLs.

### Alternative — Via sidebar
```
browser_snapshot → locate sidebar nav
browser_click    → module icon/text in sidebar
browser_wait_for → page finishes loading
```

---

## Form Interactions

### Text Input
```
browser_click → input field
browser_type  → [value to enter]
```

### Custom Dropdown (not a native select)
```
browser_click    → dropdown trigger button
browser_wait_for → dropdown menu opens
browser_snapshot → confirm options are visible
browser_click    → the option to select
```

### Native `<select>` Dropdown
```
browser_select_option → [selector] → [value or label]
```

### Date Picker
```
browser_click → date input field
browser_type  → [YYYY-MM-DD format]
# If custom date picker does not accept direct input:
browser_click    → date picker icon/trigger
browser_snapshot → view calendar popup
browser_click    → the day to select
```

### Checkbox / Toggle
```
browser_check → [checkbox selector]
# For custom toggle buttons:
browser_click → [toggle selector]
```

---

## Verifying Results After an Action

### After clicking Save / Submit
```
browser_wait_for  → spinner/loading disappears
browser_snapshot  → check:
  - Success toast visible?    → ✅ action succeeded
  - Error message visible?    → ❌ record exact error text
  - URL changed?              → indicates navigation to another page
browser_screenshot → capture the state
```

### After navigating to a page
```
browser_snapshot → read accessibility tree, check:
  - Page title (h1) is correct?
  - Main element of the module is present?
  - Any error page (404, 403)?
```

---

## Finding an Element When Selector is Unknown

**Step 1**: `browser_snapshot` → get full accessibility tree
**Step 2**: Search the tree by:
- Text content: `"Save"`, `"Submit"`, `"Cancel"`
- Role: `button`, `link`, `textbox`, `combobox`
- Label: `aria-label` attributes

**Step 3**: Use text selector or role selector:
```
browser_click → element with text "Save"
browser_click → button with label "Add Employee"
```

> See `../01_navigation/common_selectors.md` for a list of reusable selectors.

---

## Handling Modals / Dialogs

```
# Open modal
browser_click    → button that triggers the modal
browser_wait_for → modal appears ([role="dialog"])
browser_snapshot → read modal content

# Interact inside modal
browser_click → elements inside modal
browser_type  → values to enter

# Close modal
browser_click    → Confirm/Save or Cancel/Close button inside modal
browser_wait_for → modal disappears
```

---

## When to Take Screenshots

| Timing | Reason |
|--------|--------|
| After login | Confirm valid session |
| Before each major action | Baseline state |
| After each major action | Verify result |
| When an error appears | Capture bug evidence |
| When test PASSES | Proof of pass |
| When test FAILS | Proof of failure |

---

## Wait Rules — Critical

> ❌ **NEVER** use fixed sleep/wait (e.g., 3 seconds, 5 seconds)
> ✅ **ALWAYS** wait based on element state or network condition

```
✅ browser_wait_for → spinner disappears
✅ browser_wait_for → success message appears
✅ browser_wait_for → URL changes
✅ browser_snapshot → verify state before next action
```

---

## When an Element Cannot Be Found

Checklist before reporting as a bug:
1. `browser_snapshot` — is the element truly absent from the page?
2. Check role — see `../04_roles_permissions/role_matrix.md` — the role may not have access
3. Scroll down — element may be outside viewport: use `browser_scroll`
4. Wait for load — page may still be loading: use `browser_wait_for`
5. Check URL — are you on the correct page?
