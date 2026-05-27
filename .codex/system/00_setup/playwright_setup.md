# Playwright MCP â€” How the Agent Interacts with HRcloud

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
1. browser_navigate â†’ https://app.hrcloud.com/login
2. browser_snapshot â†’ confirm login form is visible
3. browser_click    â†’ email input field
4. browser_type     â†’ [email address]
5. browser_click    â†’ password input field
6. browser_type     â†’ [password]
7. browser_click    â†’ "Log In" / "Sign In" button
8. browser_wait_for â†’ URL contains "/dashboard" OR dashboard element appears
9. browser_screenshot â†’ confirm successful login
```

---

## Navigating to a Module

### Fastest method â€” Direct URL
```
browser_navigate  â†’ [module URL from url_map.md]
browser_wait_for  â†’ main element of the module appears
browser_screenshot â†’ confirm you are on the correct page
```

> See `../01_navigation/url_map.md` for all module URLs.

### Alternative â€” Via sidebar
```
browser_snapshot â†’ locate sidebar nav
browser_click    â†’ module icon/text in sidebar
browser_wait_for â†’ page finishes loading
```

---

## Form Interactions

### Text Input
```
browser_click â†’ input field
browser_type  â†’ [value to enter]
```

### Custom Dropdown (not a native select)
```
browser_click    â†’ dropdown trigger button
browser_wait_for â†’ dropdown menu opens
browser_snapshot â†’ confirm options are visible
browser_click    â†’ the option to select
```

### Native `<select>` Dropdown
```
browser_select_option â†’ [selector] â†’ [value or label]
```

### Date Picker
```
browser_click â†’ date input field
browser_type  â†’ [YYYY-MM-DD format]
# If custom date picker does not accept direct input:
browser_click    â†’ date picker icon/trigger
browser_snapshot â†’ view calendar popup
browser_click    â†’ the day to select
```

### Checkbox / Toggle
```
browser_check â†’ [checkbox selector]
# For custom toggle buttons:
browser_click â†’ [toggle selector]
```

---

## Verifying Results After an Action

### After clicking Save / Submit
```
browser_wait_for  â†’ spinner/loading disappears
browser_snapshot  â†’ check:
  - Success toast visible?    â†’ âœ… action succeeded
  - Error message visible?    â†’ âŒ record exact error text
  - URL changed?              â†’ indicates navigation to another page
browser_screenshot â†’ capture the state
```

### After navigating to a page
```
browser_snapshot â†’ read accessibility tree, check:
  - Page title (h1) is correct?
  - Main element of the module is present?
  - Any error page (404, 403)?
```

---

## Finding an Element When Selector is Unknown

**Step 1**: `browser_snapshot` â†’ get full accessibility tree
**Step 2**: Search the tree by:
- Text content: `"Save"`, `"Submit"`, `"Cancel"`
- Role: `button`, `link`, `textbox`, `combobox`
- Label: `aria-label` attributes

**Step 3**: Use text selector or role selector:
```
browser_click â†’ element with text "Save"
browser_click â†’ button with label "Add Employee"
```

> See `../01_navigation/common_selectors.md` for a list of reusable selectors.

---

## Handling Modals / Dialogs

```
# Open modal
browser_click    â†’ button that triggers the modal
browser_wait_for â†’ modal appears ([role="dialog"])
browser_snapshot â†’ read modal content

# Interact inside modal
browser_click â†’ elements inside modal
browser_type  â†’ values to enter

# Close modal
browser_click    â†’ Confirm/Save or Cancel/Close button inside modal
browser_wait_for â†’ modal disappears
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

## Wait Rules â€” Critical

> âŒ **NEVER** use fixed sleep/wait (e.g., 3 seconds, 5 seconds)
> âœ… **ALWAYS** wait based on element state or network condition

```
âœ… browser_wait_for â†’ spinner disappears
âœ… browser_wait_for â†’ success message appears
âœ… browser_wait_for â†’ URL changes
âœ… browser_snapshot â†’ verify state before next action
```

---

## When an Element Cannot Be Found

Checklist before reporting as a bug:
1. `browser_snapshot` â€” is the element truly absent from the page?
2. Check role â€” see `../04_roles_permissions/role_matrix.md` â€” the role may not have access
3. Scroll down â€” element may be outside viewport: use `browser_scroll`
4. Wait for load â€” page may still be loading: use `browser_wait_for`
5. Check URL â€” are you on the correct page?

