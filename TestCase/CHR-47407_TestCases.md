# CHR-47407 — Perform | Cycle | Edit Action | Redesign
**Total: 57 Test Cases** | P0: 8 | P1: 38 | P2: 8 | P3: 3

> ⚠️ TC_027, TC_028, TC_046 removed (duplicates). TC_058–TC_060 added (new coverage).
> ⚠️ TC_037 blocked pending BA confirmation on final One-Time cycle popup wording.

---

## Suite 1: Permissions & Access Control

---

**TC_PERFORM_CYCLE_EDIT_001**
- **Title:** Verify authorized user can access Edit button and open cycle builder on active cycle
- **Priority:** P0 | **Type:** Positive | **Ref:** AC1
- **Preconditions:**
  - User has Perform admin / authorized role
  - At least one active cycle exists in Perform → Cycle list
- **Steps:**
  1. Login with authorized user account
  2. Navigate to Perform → Cycle
  3. Locate an active cycle in the list
  4. Observe the Edit button
  5. Click Edit
- **Expected Results:**
  - Edit button is visible on the active cycle
  - Full cycle builder opens with all fields loaded correctly
  - No error or restriction message is displayed

---

**TC_PERFORM_CYCLE_EDIT_002**
- **Title:** Verify non-authorized user does NOT see Edit button on any cycle
- **Priority:** P0 | **Type:** Security | **Ref:** AC1
- **Preconditions:**
  - User has a role without cycle edit permission (e.g. employee, viewer)
  - At least one cycle exists
- **Steps:**
  1. Login with non-authorized user account
  2. Navigate to Perform → Cycle
  3. Observe the cycle list UI
- **Expected Results:**
  - No Edit button appears on any cycle
  - User sees read-only view of cycle information only

---

**TC_PERFORM_CYCLE_EDIT_003**
- **Title:** Verify non-authorized user accessing Edit URL directly is blocked and shown read-only view
- **Priority:** P0 | **Type:** Security | **Ref:** AC1
- **Preconditions:**
  - Non-authorized user has the direct edit URL (e.g. /perform/cycles/{id}/edit)
- **Steps:**
  1. Login with non-authorized user account
  2. Paste the direct edit URL into the browser address bar and navigate
  3. Observe the result
- **Expected Results:**
  - User is redirected or shown access denied / read-only view
  - User cannot make any changes to the cycle

---

**TC_PERFORM_CYCLE_EDIT_004**
- **Title:** Verify authorized user can access Edit on both active and inactive cycles
- **Priority:** P1 | **Type:** Positive | **Ref:** AC1, AC11
- **Preconditions:**
  - Authorized user
  - At least one active cycle and one inactive cycle exist
- **Steps:**
  1. Navigate to Perform → Cycle
  2. Click Edit on an active cycle → observe cycle builder opens
  3. Navigate back to Cycle list
  4. Click Edit on an inactive cycle → observe cycle builder opens
- **Expected Results:**
  - Both active and inactive cycles open the full cycle builder without restriction
  - No deactivation requirement message is displayed

---

## Suite 2: Entry Point & Navigation

---

**TC_PERFORM_CYCLE_EDIT_005**
- **Title:** Verify Save on inactive cycle redirects to cycle list, shows toast, and updates incomplete tasks
- **Priority:** P0 | **Type:** Positive | **Ref:** AC2, AC11
- **Preconditions:**
  - Authorized user
  - Inactive cycle with at least one incomplete task and one completed task
- **Steps:**
  1. Navigate to Perform → Cycle → click Edit on inactive cycle
  2. Change the Description field
  3. Click Save
  4. After redirect, re-open the cycle and check incomplete task details
  5. Check completed task details
- **Expected Results:**
  - User is redirected to Cycle list
  - Toast message appears confirming save
  - Incomplete task reflects the updated Description
  - Completed task remains in last submitted/saved state (unchanged)

---

**TC_PERFORM_CYCLE_EDIT_006**
- **Title:** Verify Cancel with unsaved changes shows Discard confirmation popup
- **Priority:** P1 | **Type:** Positive | **Ref:** AC2
- **Preconditions:**
  - Authorized user in Edit cycle page
  - At least one field has been changed but not saved
- **Steps:**
  1. Open Edit on any cycle
  2. Change the Title field
  3. Click Cancel
- **Expected Results:**
  - Popup appears: "Do you want to discard changes? Any unsaved changes will be lost."
  - Two action buttons visible: **Discard** and **Take me back**

---

**TC_PERFORM_CYCLE_EDIT_007**
- **Title:** Verify "Discard" in cancel popup navigates to cycle list and discards all unsaved changes
- **Priority:** P1 | **Type:** Positive | **Ref:** AC2
- **Preconditions:**
  - Discard confirmation popup is open (from TC_006)
- **Steps:**
  1. Click **Discard** in the popup
- **Expected Results:**
  - User is navigated to Cycle list
  - Unsaved changes are NOT persisted
  - Cycle data remains as it was before editing

---

**TC_PERFORM_CYCLE_EDIT_008**
- **Title:** Verify "Take me back" in cancel popup returns user to edit form with all unsaved changes intact
- **Priority:** P1 | **Type:** Positive | **Ref:** AC2
- **Preconditions:**
  - Discard confirmation popup is open
- **Steps:**
  1. Click **Take me back** in the popup
- **Expected Results:**
  - User is returned to the edit cycle form
  - All unsaved changes are still present in the form fields

---

## Suite 3: Save Decision Logic

---

**TC_PERFORM_CYCLE_EDIT_009**
- **Title:** Verify Save on inactive cycle with immediate field changed does NOT show popup but DOES update incomplete tasks
- **Priority:** P0 | **Type:** Positive | **Ref:** AC3, AC11
- **Preconditions:**
  - Authorized user
  - Inactive cycle with at least one incomplete task and one completed task
- **Steps:**
  1. Open Edit on inactive (not running) cycle
  2. Change the Title to "Updated Cycle Title"
  3. Click Save
  4. Re-open the cycle and inspect the task list
  5. Check incomplete task name
  6. Check completed task state
- **Expected Results:**
  - Save Review popup does **NOT** appear
  - System saves directly
  - Incomplete task name is updated to reflect "Updated Cycle Title"
  - Completed task remains in last submitted/saved state (no change)
  - Toast: "Changes saved for the next cycle."

---

**TC_PERFORM_CYCLE_EDIT_010**
- **Title:** Verify Save on active running cycle with ONLY future-only fields changed does NOT show popup
- **Priority:** P0 | **Type:** Positive | **Ref:** AC3, AC7
- **Preconditions:**
  - Active cycle with a running run
  - Authorized user
- **Steps:**
  1. Open Edit on active running cycle
  2. Change the Overall Rating toggle (future-only field)
  3. Click Save
- **Expected Results:**
  - Popup does **NOT** appear
  - System saves directly
  - Toast: "Changes saved for the next cycle."
  - Running tasks are not modified

---

**TC_PERFORM_CYCLE_EDIT_011**
- **Title:** Verify Save on active running cycle with at least one immediate field changed shows Review popup
- **Priority:** P0 | **Type:** Positive | **Ref:** AC3, AC5
- **Preconditions:**
  - Active cycle with at least one incomplete running task
  - Authorized user
- **Steps:**
  1. Open Edit on active running cycle
  2. Change Notification Settings (immediate field)
  3. Click Save
- **Expected Results:**
  - Popup titled "Review your changes" is displayed
  - Message: "Some changes can apply now, while others take effect starting next cycle."
  - List shows "Notification Settings" as changed immediate field
  - Three action buttons: **Apply changes now**, **Save for next cycle**, **x**

---

**TC_PERFORM_CYCLE_EDIT_012**
- **Title:** Verify "Apply changes now" applies changes to incomplete tasks only and shows correct toast
- **Priority:** P0 | **Type:** Positive | **Ref:** AC3, AC6, AC10
- **Preconditions:**
  - Review popup is open (immediate field changed on active running cycle)
  - Cycle has at least one incomplete task and one completed task
- **Steps:**
  1. From Review popup, click **Apply changes now**
  2. After redirect, inspect incomplete task
  3. Inspect completed task
- **Expected Results:**
  - Immediate field changes are applied to incomplete tasks of the last running run
  - Completed tasks remain unchanged
  - User is redirected to Cycle list
  - Toast: "Eligible changes were applied to running tasks. Other changes were saved for the next cycle. Completed tasks were not changed."

---

**TC_PERFORM_CYCLE_EDIT_013**
- **Title:** Verify "Save for next cycle" does not modify any running tasks and shows correct toast
- **Priority:** P0 | **Type:** Positive | **Ref:** AC3, AC10
- **Preconditions:**
  - Review popup is open
- **Steps:**
  1. From Review popup, click **Save for next cycle**
  2. After redirect, inspect running tasks
- **Expected Results:**
  - No running tasks are modified
  - No trigger is fired
  - User is redirected to Cycle list
  - Toast: "Changes saved for the next cycle. Current running tasks were not changed."

---

**TC_PERFORM_CYCLE_EDIT_014**
- **Title:** Verify clicking "x" on Review popup closes it and returns to edit form without saving
- **Priority:** P1 | **Type:** Positive | **Ref:** AC3, AC5
- **Preconditions:**
  - Review popup is open
- **Steps:**
  1. Click the **x** (close) button on the Review popup
- **Expected Results:**
  - Popup closes
  - User is returned to the edit cycle form
  - All changes are still present in the form
  - No save is performed

---

## Suite 4: Immediate Update Fields

---

**TC_PERFORM_CYCLE_EDIT_015**
- **Title:** Verify Title change after "Apply changes now" is reflected in BOTH incomplete and completed tasks
- **Priority:** P1 | **Type:** Positive | **Ref:** AC4
- **Preconditions:**
  - Active running cycle with at least one incomplete task and one completed task
- **Steps:**
  1. Note the current task name (e.g. "Q1 Review")
  2. Open Edit → change cycle Title to "Q1 Performance Review 2026"
  3. Click Save → popup appears → click **Apply changes now**
  4. Navigate into task list and inspect an incomplete task's name
  5. Inspect a completed task's name
- **Expected Results:**
  - Incomplete task name = "Q1 Performance Review 2026"
  - Completed task name = "Q1 Performance Review 2026"
  - Title is the exception — it applies to both incomplete and completed tasks

---

**TC_PERFORM_CYCLE_EDIT_016**
- **Title:** Verify Description change after "Apply changes now" is reflected in BOTH incomplete and completed tasks and visible in audit
- **Priority:** P1 | **Type:** Positive | **Ref:** AC4
- **Preconditions:**
  - Active running cycle with incomplete and completed tasks
- **Steps:**
  1. Open Edit → change Description to "Updated description text"
  2. Click Save → Apply changes now
  3. Open incomplete task details and check description
  4. Open completed task details and check description
  5. Check audit log of completed task
- **Expected Results:**
  - Incomplete task description = "Updated description text"
  - Completed task description = "Updated description text"
  - Audit log of task/review shows the description update

---

**TC_PERFORM_CYCLE_EDIT_017**
- **Title:** Verify Notification Settings change applies ONLY to incomplete tasks; completed tasks retain original state
- **Priority:** P1 | **Type:** Positive | **Ref:** AC4
- **Preconditions:**
  - Active running cycle with incomplete and completed tasks
  - Note current notification state of a completed task before editing
- **Steps:**
  1. Open Edit → change Notification Settings (e.g. toggle email notifications ON)
  2. Click Save → Apply changes now
  3. Inspect notification settings on an incomplete task
  4. Inspect notification settings on a completed task
- **Expected Results:**
  - Incomplete task: email notifications enabled (updated to new setting)
  - Completed task: notification state unchanged (original state preserved)
  - No stage restriction applied to this field

---

**TC_PERFORM_CYCLE_EDIT_018**
- **Title:** Verify End Date change is treated as immediate field when review period has NOT yet passed
- **Priority:** P1 | **Type:** Positive | **Ref:** AC4
- **Preconditions:**
  - Active cycle with Custom Date Review
  - Review period end date is in the future
- **Steps:**
  1. Open Edit → change End Date to a different valid future date
  2. Click Save
  3. Observe whether popup appears and what it lists
  4. Select Apply changes now
- **Expected Results:**
  - Review popup appears
  - "End Date" is listed in the immediate fields section of the popup
  - After Apply changes now → incomplete tasks updated with new End Date

---

**TC_PERFORM_CYCLE_EDIT_019**
- **Title:** Verify End Date change is treated as FUTURE-ONLY (field remains editable) when review period has already passed
- **Priority:** P2 | **Type:** Negative | **Ref:** AC4
- **Preconditions:**
  - Active cycle with Custom Date Review
  - Review period end date has already passed
- **Steps:**
  1. Open Edit cycle and observe the End Date field state
  2. Change End Date to a new value
  3. Click Save → observe popup behavior and task state
- **Expected Results:**
  - End Date field is **still editable** (NOT disabled)
  - End Date does **NOT appear** in the popup's immediate fields list
  - Change is treated as future-only → saved for next cycle
  - Running tasks are NOT updated with the new End Date

---

**TC_PERFORM_CYCLE_EDIT_020**
- **Title:** Verify Reviewee Visibility change applies ONLY to incomplete tasks after "Apply changes now"
- **Priority:** P1 | **Type:** Positive | **Ref:** AC4
- **Preconditions:**
  - Active running cycle with incomplete and completed tasks
  - Note current Reviewee Visibility state of a completed task
- **Steps:**
  1. Open Edit → change Reviewee Visibility setting
  2. Click Save → Apply changes now
  3. Inspect incomplete task Reviewee Visibility
  4. Inspect completed task Reviewee Visibility
- **Expected Results:**
  - Incomplete task: Reviewee Visibility updated to new setting
  - Completed task: original Reviewee Visibility state retained unchanged

---

## Suite 5: Save Review Popup Content & Behavior

---

**TC_PERFORM_CYCLE_EDIT_021**
- **Title:** Verify popup only lists immediate fields that were actually changed by user (not all immediate fields)
- **Priority:** P1 | **Type:** Positive | **Ref:** AC5
- **Preconditions:**
  - Active running cycle
- **Steps:**
  1. Open Edit → change ONLY Notification Settings (leave Title, End Date untouched)
  2. Click Save → observe popup
  3. Read the list in popup
- **Expected Results:**
  - Popup list shows only "Notification Settings"
  - Title and End Date do NOT appear (they were not changed)

---

**TC_PERFORM_CYCLE_EDIT_022**
- **Title:** Verify Stage and Notification Settings appear as SEPARATE popup entries when both changed in Review Options section
- **Priority:** P1 | **Type:** Edge Case | **Ref:** AC5
- **Preconditions:**
  - Active running cycle with Custom Date Review (stages configured)
- **Steps:**
  1. Open Edit → change both a Review Options stage toggle AND Notification Settings
  2. Click Save → observe popup list
- **Expected Results:**
  - Popup shows "Stage" and "Notification Settings" as two distinct separate list entries
  - They are NOT merged into a single "Review Options" item

---

**TC_PERFORM_CYCLE_EDIT_023**
- **Title:** Verify popup title and message text exactly match specified wording (single message only)
- **Priority:** P1 | **Type:** UI/UX | **Ref:** AC5
- **Preconditions:**
  - Active running cycle with at least one immediate field changed
- **Steps:**
  1. Edit cycle → change an immediate field → click Save
  2. Popup appears → read the title and message text carefully
- **Expected Results:**
  - Title: **"Review your changes"**
  - Message: **"Some changes can apply now, while others take effect starting next cycle."**
  - Only ONE message displayed (no second helper text message)

---

**TC_PERFORM_CYCLE_EDIT_024**
- **Title:** Verify popup does NOT appear when only future-only fields are changed (e.g. Questions)
- **Priority:** P1 | **Type:** Negative | **Ref:** AC5
- **Preconditions:**
  - Active running cycle
- **Steps:**
  1. Open Edit → add or edit a Question (future-only field)
  2. Click Save
- **Expected Results:**
  - Review popup does **NOT** appear
  - System saves directly
  - Toast: "Changes saved for the next cycle."

---

**TC_PERFORM_CYCLE_EDIT_025**
- **Title:** Verify popup lists all changed immediate fields when user changes multiple at once
- **Priority:** P2 | **Type:** Positive | **Ref:** AC5
- **Preconditions:**
  - Active running cycle
- **Steps:**
  1. Open Edit → change Title, Notification Settings, AND Reviewee Visibility
  2. Click Save → observe popup list
- **Expected Results:**
  - Popup list includes: Title, Notification Settings, Reviewee Visibility
  - Only those 3 fields — no others appear

---

## Suite 6: Future-Only Fields

---

**TC_PERFORM_CYCLE_EDIT_026**
- **Title:** Verify Goal Tracking change on active running cycle saves for next cycle without popup
- **Priority:** P1 | **Type:** Positive | **Ref:** AC7
- **Preconditions:**
  - Active running cycle
- **Steps:**
  1. Open Edit → change Goal Tracking setting
  2. Click Save
- **Expected Results:**
  - Popup does **NOT** appear
  - Save succeeds
  - Toast: "Changes saved for the next cycle."
  - Running tasks are not affected

---

**TC_PERFORM_CYCLE_EDIT_029**
- **Title:** Verify changing both immediate and future-only fields triggers popup listing ONLY immediate fields; future fields save silently
- **Priority:** P1 | **Type:** Edge Case | **Ref:** AC3, AC5, AC7
- **Preconditions:**
  - Active running cycle
- **Steps:**
  1. Open Edit → change Title (immediate) AND Overall Rating config (future-only)
  2. Click Save → observe popup
  3. Select Apply changes now
  4. Verify task title
  5. Verify Overall Rating on tasks
- **Expected Results:**
  - Popup appears (because Title is immediate)
  - Popup list: only "Title" — Overall Rating is NOT listed
  - After Apply changes now: Title updated on incomplete tasks; Overall Rating saved for next cycle only

---

## Suite 7: Stage-Based Behavior

---

**TC_PERFORM_CYCLE_EDIT_030**
- **Title:** Verify all Review Options toggles are editable before first stage trigger date (Custom Date Review)
- **Priority:** P1 | **Type:** Positive | **Ref:** AC9, AC12
- **Preconditions:**
  - Active cycle with Schedule Type = Custom Date Review
  - Current date is before the first stage trigger date
- **Steps:**
  1. Open Edit → navigate to Review Options section
  2. Attempt to interact with Self, Manager, Peer, Direct Report toggles
- **Expected Results:**
  - All four toggles are editable
  - No disabled state or tooltip shown

---

**TC_PERFORM_CYCLE_EDIT_031**
- **Title:** Verify Peer and Direct Report toggles are DISABLED after their trigger dates pass (Custom Date Review)
- **Priority:** P1 | **Type:** Positive | **Ref:** AC9, AC12
- **Preconditions:**
  - Active Custom Date Review cycle
  - Review Period: e.g. Mar 3 – Apr 15; Peer/DR trigger = Mar 16
  - Current date > Mar 16 but Self/Manager stage not yet started
- **Steps:**
  1. Open Edit → navigate to Review Options
  2. Attempt to interact with all four toggles
  3. Hover over a disabled toggle
- **Expected Results:**
  - Self and Manager toggles: editable
  - Peer and Direct Report toggles: **disabled**
  - Tooltip: "This review stage has already started; participants are already set."

---

**TC_PERFORM_CYCLE_EDIT_032**
- **Title:** Verify ALL Review Options toggles are disabled when all stages have started (Custom Date Review)
- **Priority:** P1 | **Type:** Positive | **Ref:** AC9, AC12
- **Preconditions:**
  - Active Custom Date Review cycle
  - Current date > all four stage trigger dates
- **Steps:**
  1. Open Edit → navigate to Review Options
  2. Attempt to interact with all four toggles
  3. Hover over each disabled toggle
- **Expected Results:**
  - All four toggles (Self, Manager, Peer, DR) are **disabled**
  - Correct tooltip on each: "This review stage has already started; participants are already set."

---

**TC_PERFORM_CYCLE_EDIT_033**
- **Title:** Verify Anniversary Date Review has NO stage-based locking and Review Options changes are treated as future-only
- **Priority:** P1 | **Type:** Positive | **Ref:** AC9, AC12
- **Preconditions:**
  - Active cycle with Schedule Type = Anniversary Date Review and a running run
- **Steps:**
  1. Open Edit → navigate to Review Options
  2. Observe toggle states
  3. Change a Review Options toggle
  4. Click Save → observe popup and behavior
- **Expected Results:**
  - All Review Options toggles are **editable** (no stage-based locking)
  - No stage-based tooltip shown
  - Review Options change is treated as **future-only** → popup does NOT appear for this change
  - Toast: "Changes saved for the next cycle." (if no other immediate fields changed)

---

**TC_PERFORM_CYCLE_EDIT_034**
- **Title:** Verify recurring cycle calculates stage editability independently PER RUN (not globally)
- **Priority:** P1 | **Type:** Edge Case | **Ref:** AC12
- **Preconditions:**
  - Recurring cycle: Cycle 1 (Mar 3 – Apr 15), Cycle 2 (Apr 15 – Aug 15)
  - Current date: Cycle 1 stages have passed; Cycle 2 stages have NOT yet started
- **Steps:**
  1. Open Edit on the recurring cycle
  2. Navigate to Review Options
  3. Observe toggle editability relative to Cycle 2's stage trigger dates
- **Expected Results:**
  - Editability is evaluated based on Cycle 2's own stage trigger dates
  - All toggles are editable (Cycle 2 has not started any stage)
  - Cycle 1's passed stages do NOT influence Cycle 2's editability

---

## Suite 8: Short Cycle Handling

---

**TC_PERFORM_CYCLE_EDIT_035**
- **Title:** Verify helper text appears and stage offsets are overridden when review period duration is less than 15 days
- **Priority:** P2 | **Type:** Positive | **Ref:** AC12
- **Preconditions:**
  - Edit mode on a Custom Date Review cycle
- **Steps:**
  1. Open Edit → set review period to less than 15 days (e.g. Start Apr 7, End Apr 14 = 7 days)
  2. Observe UI near the review period field
- **Expected Results:**
  - Helper text: "The duration of your review period is less than 15 days. Tasks will be triggered at its start."
  - All stage offsets overridden: all stages triggered at start of cycle (day 0)

---

**TC_PERFORM_CYCLE_EDIT_036**
- **Title:** Verify existing stage offsets (e.g. 30 days / 15 days) are NOT preserved when duration drops below 15 days
- **Priority:** P2 | **Type:** Negative | **Ref:** AC12
- **Preconditions:**
  - Cycle with existing stage offsets configured (30-day and 15-day offsets)
- **Steps:**
  1. Open Edit → reduce review period to < 15 days
  2. Inspect stage trigger configuration
- **Expected Results:**
  - Previous offset values (30 days, 15 days) are **not preserved**
  - System overrides all stages to trigger at start (day 0)
  - No previous offset values reused or carried over

---

## Suite 9: One-Time Cycle Behavior

---

**TC_PERFORM_CYCLE_EDIT_037**
- **Title:** Verify editing One-Time active cycle with running run shows popup for immediate field changes
- **Priority:** P1 | **Type:** Positive | **Ref:** AC3
- **⚠️ BLOCKED:** Pending BA confirmation on final popup wording ("future generated tasks" vs "next cycle"). Confirm story/design is updated before executing.
- **Preconditions:**
  - One-Time cycle that is active with at least one incomplete running task
  - Authorized user
- **Steps:**
  1. Open Edit on One-Time active cycle
  2. Change Notification Settings (immediate field)
  3. Click Save → observe popup
  4. Click Apply changes now → observe incomplete tasks
  5. Re-run: Click Save for next cycle → observe task state
- **Expected Results:**
  - Review popup appears (same logic as Recurring)
  - Popup wording uses "future generated tasks" NOT "next run"
  - Apply changes now → incomplete tasks updated
  - Save for next cycle → tasks unchanged; changes apply to future manual assignments

---

**TC_PERFORM_CYCLE_EDIT_038**
- **Title:** Verify editing One-Time cycle that has NOT yet started saves directly without popup
- **Priority:** P1 | **Type:** Positive | **Ref:** AC3
- **Preconditions:**
  - One-Time cycle that has not started (inactive / no running tasks)
- **Steps:**
  1. Open Edit on not-started One-Time cycle
  2. Change any field (immediate or future-only)
  3. Click Save
- **Expected Results:**
  - Popup does **NOT** appear
  - System saves directly
  - Toast message is shown

---

**TC_PERFORM_CYCLE_EDIT_039**
- **Title:** Verify editing a completed One-Time cycle saves as future config without popup
- **Priority:** P1 | **Type:** Edge Case | **Ref:** AC3
- **Preconditions:**
  - One-Time cycle that is completed (no running run, all tasks done)
- **Steps:**
  1. Open Edit on completed One-Time cycle
  2. Change an immediate field (e.g. Notification Settings)
  3. Click Save
- **Expected Results:**
  - Popup does **NOT** appear (no running cycle)
  - System saves config change
  - Changes apply to future manual assignments only
  - Toast: "Changes saved for the next cycle."

---

## Suite 10: Multiple Edits & Manual Assignment

---

**TC_PERFORM_CYCLE_EDIT_040**
- **Title:** Verify manual assignment created after "Save for next cycle" uses LATEST saved config (not old version)
- **Priority:** P1 | **Type:** Integration | **Ref:** AC12, CHR-48715
- **Preconditions:**
  - Active cycle (recurring or one-time)
  - Edit has been performed and "Save for next cycle" was selected
- **Steps:**
  1. Edit cycle → make config changes → Save for next cycle
  2. Immediately create a manual assignment for an employee in that cycle
  3. Open the newly created assignment task and check its configuration
- **Expected Results:**
  - Manual assignment task uses the **latest saved config** (post-edit version)
  - Old pre-edit config is NOT used
  - True for both Recurring and One-Time cycles

---

**TC_PERFORM_CYCLE_EDIT_041**
- **Title:** Verify second edit overwrites first pending future config (latest save is always source of truth)
- **Priority:** P1 | **Type:** Edge Case | **Ref:** AC12, Comments
- **Preconditions:**
  - Active cycle with running run
- **Steps:**
  1. Edit 1: Change Title to "Version A" → click Save → select **Save for next cycle**
  2. Edit 2: Change Title to "Version B" → click Save → select **Apply changes now**
  3. Verify title of running incomplete tasks
  4. Verify config stored for future (next run / manual assignment)
- **Expected Results:**
  - Running incomplete tasks title = "Version B"
  - Future config (next run / manual assignment) = "Version B"
  - "Version A" is fully **overwritten** — only one pending future configuration exists

---

**TC_PERFORM_CYCLE_EDIT_042**
- **Title:** Verify Future-then-Immediate edit sequence: Immediate (Version B) overwrites all previous pending Future config (Version A)
- **Priority:** P1 | **Type:** Edge Case | **Ref:** AC12, Comments
- **Preconditions:**
  - Active running cycle
- **Steps:**
  1. Edit 1: Change Goal Tracking (future-only) → Save (Version A saved for next cycle)
  2. Edit 2: Change Notification Settings (immediate) → Save → Apply changes now (Version B)
  3. Verify running tasks
  4. Verify pending future config for manual assignment
- **Expected Results:**
  - Running tasks: Notification Settings = Version B (updated)
  - Future config: latest saved = Version B (Version A overwritten)
  - No conflict between current and future state

---

## Suite 11: Toast Messages

---

**TC_PERFORM_CYCLE_EDIT_043**
- **Title:** Verify toast message after "Apply changes now" matches exact specified text
- **Priority:** P1 | **Type:** UI/UX | **Ref:** AC10
- **Steps:**
  1. Edit active running cycle → change an immediate field → Save → click **Apply changes now**
  2. Observe the toast message text after redirect
- **Expected Results:**
  - Toast: **"Eligible changes were applied to running tasks. Other changes were saved for the next cycle. Completed tasks were not changed."**

---

**TC_PERFORM_CYCLE_EDIT_044**
- **Title:** Verify toast message after "Save for next cycle" matches exact specified text
- **Priority:** P1 | **Type:** UI/UX | **Ref:** AC10
- **Steps:**
  1. Edit active running cycle → change an immediate field → Save → click **Save for next cycle**
  2. Observe the toast message text after redirect
- **Expected Results:**
  - Toast: **"Changes saved for the next cycle. Current running tasks were not changed."**

---

**TC_PERFORM_CYCLE_EDIT_045**
- **Title:** Verify toast message when only non-immediate fields changed (no popup path) matches exact text
- **Priority:** P1 | **Type:** UI/UX | **Ref:** AC10
- **Steps:**
  1. Edit active running cycle → change only future-only field (e.g. Questions) → Save
  2. Observe the toast message text after redirect
- **Expected Results:**
  - Toast: **"Changes saved for the next cycle."**

---

## Suite 12: Inactive Cycle Task Updates

---

**TC_PERFORM_CYCLE_EDIT_047**
- **Title:** Verify incomplete tasks in inactive cycle display updated info (title, review period, due date, notifications) after save
- **Priority:** P1 | **Type:** Positive | **Ref:** AC11
- **Preconditions:**
  - Inactive cycle with at least one incomplete task and one completed task
- **Steps:**
  1. Note current values: Title, Review Period dates, Due Date, Notification state of incomplete task
  2. Open Edit → change Title, review period dates, and Notification Settings
  3. Save
  4. Open cycle → inspect incomplete task details
  5. Open completed task details
- **Expected Results:**
  - Incomplete task: title updated, review period (start/end) updated, due date updated, notification setting updated
  - Completed task: all values remain in last submitted/saved state (no changes)

---

**TC_PERFORM_CYCLE_EDIT_048**
- **Title:** Verify review name in cycle grid IS updated for employee when at least one stage is incomplete (inactive cycle)
- **Priority:** P2 | **Type:** Positive | **Ref:** AC11
- **Preconditions:**
  - Inactive cycle where target employee has at least one stage incomplete
- **Steps:**
  1. Note current review name in cycle grid for the target employee
  2. Open Edit → change cycle Title → Save
  3. Observe review name in grid for that employee
- **Expected Results:**
  - Review name in grid is **updated** for the employee

---

**TC_PERFORM_CYCLE_EDIT_049**
- **Title:** Verify review name in cycle grid is NOT updated for employee when all their stages are completed (inactive cycle)
- **Priority:** P2 | **Type:** Edge Case | **Ref:** AC11
- **Preconditions:**
  - Inactive cycle where target employee has ALL stages completed
- **Steps:**
  1. Note current review name for the target employee (all stages completed)
  2. Open Edit → change cycle Title → Save
  3. Observe review name in grid for that employee
- **Expected Results:**
  - Review name in grid remains **unchanged** for this employee (all stages completed)
  - Other employees with incomplete stages may have updated names

---

## Suite 13: Timeline Preview

---

**TC_PERFORM_CYCLE_EDIT_050**
- **Title:** Verify Timeline Preview is displayed as a dropdown (not flyout) and is collapsed by default in Edit mode
- **Priority:** P1 | **Type:** UI/UX | **Ref:** AC13
- **Preconditions:**
  - Any cycle in Edit mode
- **Steps:**
  1. Open Edit on any cycle
  2. Locate the Timeline Preview section
  3. Observe: component type, default state, section title, helper text
- **Expected Results:**
  - Timeline Preview is rendered as a **dropdown** (NOT a flyout/panel)
  - **Collapsed** by default
  - Section title: "Timeline Preview"
  - Helper text: "See how review periods are calculated based on your current settings."

---

**TC_PERFORM_CYCLE_EDIT_051**
- **Title:** Verify Timeline Preview can be manually expanded to show review period preview
- **Priority:** P1 | **Type:** UI/UX | **Ref:** AC13
- **Steps:**
  1. Edit mode → Timeline Preview is collapsed
  2. Click to expand the Timeline Preview dropdown
  3. Observe content
- **Expected Results:**
  - Dropdown expands when clicked
  - Preview of review periods displayed based on current configured settings

---

**TC_PERFORM_CYCLE_EDIT_052**
- **Title:** Verify Timeline Preview shows correct empty state when review period is not yet configured
- **Priority:** P2 | **Type:** Edge Case | **Ref:** AC13
- **Preconditions:**
  - Creating a new cycle OR editing a cycle without review period configured
- **Steps:**
  1. In Create or Edit mode → do not configure review period
  2. Expand Timeline Preview
- **Expected Results:**
  - Empty state: "The review period will appear here once it's configured."

---

**TC_PERFORM_CYCLE_EDIT_053**
- **Title:** Verify Timeline Preview is available in both Create and Edit modes for active and inactive cycles
- **Priority:** P2 | **Type:** Positive | **Ref:** AC13
- **Steps:**
  1. Open Create new cycle → verify Timeline Preview section exists
  2. Open Edit on inactive cycle → verify Timeline Preview section exists
  3. Open Edit on active cycle → verify Timeline Preview section exists
- **Expected Results:**
  - Timeline Preview section is present and functional in all three scenarios

---

## Suite 14: Regression — Old Messages Removal

---

**TC_PERFORM_CYCLE_EDIT_054**
- **Title:** Verify old message "The edits will apply to the next run, not the current run." is no longer displayed anywhere in the edit flow
- **Priority:** P1 | **Type:** Regression | **Ref:** Existing Flow Alignment
- **Steps:**
  1. Open Edit on an active cycle
  2. Change any field
  3. Observe the entire edit flow: form view, save, post-save
- **Expected Results:**
  - Message "The edits will apply to the next run, not the current run." does **NOT** appear at any step
  - No validation message prevents editing an active cycle

---

**TC_PERFORM_CYCLE_EDIT_055**
- **Title:** Verify no message instructs user to deactivate the cycle before editing
- **Priority:** P1 | **Type:** Regression | **Ref:** Existing Flow Alignment
- **Steps:**
  1. Open Edit on an active cycle
  2. Observe all messages, tooltips, and notifications throughout the flow
- **Expected Results:**
  - No message says "deactivate before editing" or similar
  - No reactivation duplication warning appears
  - Edit proceeds without requiring deactivation

---

## Suite 15: Negative & Security

---

**TC_PERFORM_CYCLE_EDIT_056**
- **Title:** Verify double-clicking Save button triggers ONLY one save API call (no concurrent duplicates)
- **Priority:** P0 | **Type:** Negative | **Ref:** CHR-48706
- **Preconditions:**
  - Edit mode with at least one changed field
  - Browser devtools open (Network tab)
- **Steps:**
  1. Open Edit → change a field
  2. Double-click Save button in rapid succession
  3. Monitor Network requests
- **Expected Results:**
  - Only **one** save API call is triggered
  - No "Could Not Save Changes" error appears
  - Save completes successfully with correct toast

---

**TC_PERFORM_CYCLE_EDIT_057**
- **Title:** Verify saving with invalid data shows validation error (overriding helper text) and blocks save
- **Priority:** P2 | **Type:** Negative | **Ref:** AC12
- **Preconditions:**
  - Edit mode
- **Steps:**
  1. Open Edit → enter invalid data (e.g. End Date earlier than Start Date)
  2. Click Save
- **Expected Results:**
  - Validation error message appears (overrides any helper text for that field)
  - Save is **blocked** until valid data is entered
  - No popup or success toast appears

---

## Suite 16: New Coverage

---

**TC_PERFORM_CYCLE_EDIT_058**
- **Title:** Verify Notification Settings toggle ON→OFF removes notifications from incomplete tasks; OFF→ON adds them with new config
- **Priority:** P1 | **Type:** Positive | **Ref:** AC8, AC11
- **Preconditions:**
  - Active cycle with incomplete and completed tasks
  - Notifications currently enabled on incomplete tasks
- **Steps:**
  1. **Scenario A:** Edit cycle → toggle Notifications from **ON → OFF** → Save → Apply changes now
  2. Inspect incomplete task notification state
  3. Inspect completed task notification state
  4. **Scenario B:** Edit cycle → toggle Notifications from **OFF → ON** → configure settings → Save → Apply changes now
  5. Inspect incomplete task notification state
  6. Inspect completed task notification state
- **Expected Results:**
  - Scenario A: Notifications removed from incomplete tasks; completed tasks unchanged
  - Scenario B: Notifications added to incomplete tasks with newly configured settings; completed tasks unchanged; email template updated if changed

---

**TC_PERFORM_CYCLE_EDIT_059**
- **Title:** Verify One-Time cycle: manual assignment after "Save for next cycle" uses latest saved config
- **Priority:** P1 | **Type:** Integration | **Ref:** AC12, Comments
- **Preconditions:**
  - One-Time active cycle with running incomplete tasks
- **Steps:**
  1. Edit One-Time cycle → change config (e.g. Title, Notification Settings) → Save → select **Save for next cycle**
  2. Immediately create a manual assignment for a new employee in that cycle
  3. Open the newly created assignment task and inspect config
- **Expected Results:**
  - Running tasks remain unchanged (old config)
  - New manual assignment task uses **latest saved config** (updated Title, Notifications, etc.)
  - Old pre-edit config is NOT used for the new assignment

---

**TC_PERFORM_CYCLE_EDIT_060**
- **Title:** Verify Stage entry in popup: "Apply changes now" does NOT apply Stage changes to existing tasks; only Notification Settings applies immediately
- **Priority:** P1 | **Type:** Edge Case | **Ref:** AC5
- **Preconditions:**
  - Active Custom Date Review cycle with running run
  - Both a Stage-related toggle and Notification Settings have been changed
- **Steps:**
  1. Edit cycle → change a Review Options stage toggle AND change Notification Settings
  2. Click Save → observe popup list
  3. Select **Apply changes now**
  4. Inspect running incomplete tasks: stage participant configuration
  5. Inspect running incomplete tasks: notification settings
- **Expected Results:**
  - Popup shows "Stage" and "Notification Settings" as separate entries
  - After Apply changes now:
    - Notification Settings: **updated** on incomplete running tasks (immediate behavior)
    - Stage participants: **NOT modified** on existing tasks (Stage follows future/stage-based behavior)
    - Stage changes apply to future generated tasks / next manually assigned tasks only

---

## Requirements Traceability Matrix

| AC | Requirement | Test Case IDs | Status |
|---|---|---|---|
| AC1 | Permissions | TC_001, TC_002, TC_003, TC_004 | ✅ Covered |
| AC2 | Navigation & Cancel | TC_005, TC_006, TC_007, TC_008 | ✅ Covered |
| AC3 | Save Decision Logic | TC_009, TC_010, TC_011, TC_012, TC_013, TC_014, TC_037, TC_038, TC_039 | ✅ Covered |
| AC4 | Immediate Update Fields | TC_015, TC_016, TC_017, TC_018, TC_019, TC_020 | ✅ Covered |
| AC5 | Save Review Popup | TC_021, TC_022, TC_023, TC_024, TC_025, TC_060 | ✅ Covered |
| AC6 | Immediate Changes Behavior | TC_012, TC_015–TC_020 | ✅ Covered |
| AC7 | Future-Only Fields | TC_024, TC_026, TC_029 | ✅ Covered |
| AC8 | Changes on Tasks | TC_015–TC_020, TC_058 | ✅ Covered |
| AC9 | Stage-Based Behavior | TC_030, TC_031, TC_032, TC_033, TC_034 | ✅ Covered |
| AC10 | Toast Messages | TC_043, TC_044, TC_045 | ✅ Covered |
| AC11 | Inactive Cycle Behavior | TC_005, TC_009, TC_047, TC_048, TC_049 | ✅ Covered |
| AC12 | Multiple Edits / Stage / Short Cycle / Source of Truth | TC_034, TC_035, TC_036, TC_040, TC_041, TC_042, TC_057 | ✅ Covered |
| AC13 | Timeline Preview | TC_050, TC_051, TC_052, TC_053 | ✅ Covered |
| Comments | One-Time Cycle Logic | TC_037, TC_038, TC_039, TC_059 | ✅ Covered |
| Comments | Latest save = source of truth | TC_040, TC_041, TC_042, TC_059 | ✅ Covered |
| Regression | Old messages removed | TC_054, TC_055 | ✅ Covered |
| Bug refs | CHR-48706, CHR-48715 | TC_056, TC_040 | ✅ Covered |
| New | Notification toggle ON/OFF detail | TC_058 | ✅ Covered |
| New | Stage entry popup behavior | TC_060 | ✅ Covered |
