# Employee Lifecycle Workflow

**Modules Involved**: Recruit → People → Onboard → Offboard

---

## Phase 1: Recruitment (Recruit Module)

### Workflow Steps
1. **Create Job Posting** → Recruit → Jobs → "Create Job" → Fill details → Publish
2. **Applicant Applies** → Via Job Board or manually added
3. **Review Pipeline** → Move applicant through status stages (Applied → Interview → Offer)
4. **Send Offer Letter** → Recruit → Applicant profile → "Send Offer Letter" → Template filled, sent via email
5. **Applicant Signs** → Applicant signs offer via email link
6. **Hire Applicant** → Admin clicks "Hire" → Opens hire form
7. **Fill Hire Details** → Start date, position, department, manager, employment type, salary
8. **Confirm Hire** → Employee record created in **People module**

### Verification Points
- ✅ Applicant status changes to "Hired" in Recruit
- ✅ New employee appears in People module with correct data
- ✅ Employee's start date matches what was set in hire form
- ✅ Employment type, position, department, manager are all correct

---

## Phase 2: Pre-Start / Prehire (Onboard Module)

### Workflow Steps
1. **Employee visible as Prehire** in People module (hire date is in future)
2. **Onboard Checklist auto-triggers** → if configured, based on hire date
3. **Employee receives activation email** → Sets password, logs into prehire portal
4. **Employee completes pre-start tasks**:
   - Fill out personal information form
   - Upload required documents (ID, etc.)
   - Complete I-9 Section 1
   - E-sign required forms (offer letter confirmation, policies)
5. **HR completes their tasks**:
   - Complete I-9 Section 2 (employer verification)
   - Set up payroll
   - Set up IT accounts
6. **Smart Buddy** (if configured): Buddy receives their onboard tasks

### Verification Points
- ✅ Checklist assigned to correct employee on correct trigger date
- ✅ Tasks appear in correct order
- ✅ I-9 appears with both Section 1 (employee) and Section 2 (employer) fields
- ✅ E-signature task shows signature after employee signs
- ✅ Task status updates to "Completed" when done
- ✅ HR receives notifications when employee completes tasks

---

## Phase 3: Active Employment

### Employment Changes Flow (People Full feature)
1. Manager or HR initiates employment change (position, department, salary, manager)
2. In People → employee profile → Edit employment info → "Request Change"
3. Fill new values + effective date
4. Change may require approval (configurable)
5. On effective date, change takes effect
6. Integration (payroll) syncs the change

### Verification Points
- ✅ Change request visible in audit trail
- ✅ Changes take effect on the correct date
- ✅ Payroll integration receives update (if connected)
- ✅ Org chart updates with new manager/department

---

## Phase 4: Termination (Offboard Module)

### Workflow Steps
1. **Initiate Termination** → People → Employee profile → "Change Status" → "Terminate"
2. **Fill Termination Details**:
   - Termination date
   - Reason (resignation, termination, retirement, etc.)
   - Access revocation: immediately or on date
3. **Confirm** → Employee status changes to "Inactive" on the termination date
4. **Offboard Checklist triggers** (if configured)
5. **HR/Employee complete offboard tasks**:
   - Equipment return (Assets module)
   - Exit interview
   - Final documentation sign-off
6. **Payroll sync** → Termination event sent to payroll integration
7. **Account deactivated** → Employee cannot log in after termination date

### Verification Points
- ✅ Employee status is "Inactive" on termination date
- ✅ Login access is revoked correctly (immediately or on date)
- ✅ Offboard checklist is assigned
- ✅ Payroll integration receives termination event
- ✅ Employee's data is still accessible to HR (not deleted)

---

## Phase 5: Rehire

### Workflow Steps
1. Find terminated employee in People → "Inactive" filter
2. Click "Rehire" action
3. Fill new start date, position, department
4. Confirm → Employee status changes to "Prehire" (if future date) or "Active"
5. Rehire onboard checklist triggers (if configured)

### Verification Points
- ✅ Employee's historical data preserved
- ✅ Rehire checklist triggers correctly
- ✅ Previous Time Off balance reset or carried over per policy
