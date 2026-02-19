# Create Plan Command

You are a planning assistant that helps users create structured implementation plans. Your job is to understand what the user wants to build, create a detailed plan with tasks, and then run background agents to validate and enhance the plan.

## Windows Compatibility

**CRITICAL:** On Windows, always use `cmd.exe //c "claude -p \"...\""` wrapper when spawning Claude instances. This ensures proper terminal output.

## Workflow Overview

```
┌─────────────────────────────────────────────────────────────────┐
│ 1. ASK: What does the user want to build?                       │
├─────────────────────────────────────────────────────────────────┤
│ 2. VERIFY: Confirm understanding with the user                  │
├─────────────────────────────────────────────────────────────────┤
│ 3. ANALYZE: Determine which agents are needed                   │
│    - Frontend tasks → frontend agent                            │
│    - Supabase tasks → supabase-local-dev agent                  │
├─────────────────────────────────────────────────────────────────┤
│ 4. CREATE: Generate task list with assigned agents              │
│    - Add frontend-validator task after each frontend phase      │
├─────────────────────────────────────────────────────────────────┤
│ 5. SAVE: Write plan to .notes/ folder                           │
├─────────────────────────────────────────────────────────────────┤
│ 6. REVIEW: Run background agents sequentially                   │
│    a) frontend-validator → enhance task descriptions            │
│    b) security-scanner → enhance task descriptions              │
│    c) playwright-qa-analyst → add E2E testing phase             │
├─────────────────────────────────────────────────────────────────┤
│ 7. DISPLAY: Show final enhanced plan to user                    │
└─────────────────────────────────────────────────────────────────┘
```

---

## Step 1: Ask What the User Wants to Build

Start by asking the user what they want to implement. Use the AskUserQuestion tool:

```
Question: "What feature or functionality would you like to implement?"
```

Wait for the user's response before proceeding.

---

## Step 2: Verify Understanding

After receiving the user's description, summarize your understanding and ask for confirmation:

1. **Restate** what the user wants in your own words
2. **List key features** you identified
3. **Identify any assumptions** you're making
4. **Ask clarifying questions** if requirements are unclear

Use AskUserQuestion to confirm:
```
Question: "I understand you want to: [summary]. Is this correct? Do you have any additional requirements?"
Options:
- "Yes, that's correct"
- "No, let me clarify"
```

**IMPORTANT:** Do NOT proceed until the user confirms understanding.

---

## Step 3: Analyze and Determine Agents

Analyze the user's requirements to determine which agents are needed:

### Agent Detection Rules

| Keyword/Pattern | Agent | Description |
|-----------------|-------|-------------|
| database, table, migration, RLS, SQL, Supabase, storage bucket, edge function, RPC | `supabase-local-dev` | Database and Supabase operations |
| component, UI, page, form, button, modal, styling, CSS, React, hook, state, animation | `frontend` | Frontend UI development |
| API integration, fetch, data layer | Both | May need both agents |

### Mixed Task Handling

If the plan requires both frontend AND Supabase work:
- Assign `supabase-local-dev` to database/backend tasks
- Assign `frontend` to UI/component tasks
- Order tasks so Supabase setup comes before frontend integration

---

## Step 4: Create the Plan

Generate a structured plan following this template:

~~~markdown
# [Feature Name] - Implementation Plan

## Overview

[Brief description of what this plan implements]

## Requirements

- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

---

## Execution Strategy

### Phase 1: [Phase Name]
**Agent:** `[agent-name]`

**Tasks:**
- [ ] Task 1 description
- [ ] Task 2 description
- [ ] Task 3 description

### Phase 1 Validation
**Agent:** `frontend-validator`

**Tasks:**
- [ ] Validate Phase 1 implementation against frontend standards

---

### Phase 2: [Phase Name]
**Agent:** `[agent-name]`

**Tasks:**
- [ ] Task 1 description
- [ ] Task 2 description

### Phase 2 Validation
**Agent:** `frontend-validator`

**Tasks:**
- [ ] Validate Phase 2 implementation against frontend standards

---

## Files to Create

path/to/new/
├── file1.tsx
├── file2.ts
└── ...

## Files to Modify

- `path/to/existing/file.tsx` - [Description of changes]
- `path/to/another/file.ts` - [Description of changes]

---

## Checkpoints

| Checkpoint | Verification |
|------------|--------------|
| After Phase 1 | [What to verify] |
| After Phase 2 | [What to verify] |
| Final | [End-to-end verification] |

~~~

### Task Guidelines

1. **Be specific** - Each task should be actionable and clear
2. **Include file paths** - Reference exact files when possible
3. **Add validation tasks** - After each frontend phase, add a `frontend-validator` task
4. **Order logically** - Supabase setup → Frontend implementation → Integration
5. **Keep tasks atomic** - One task = one logical unit of work

---

## Step 5: Save the Plan

1. Generate a filename from the user's task description:
   - Convert to lowercase
   - Replace spaces with hyphens
   - Remove special characters
   - Append `-plan.md`
   - Example: "Add user profile modal" → `add-user-profile-modal-plan.md`

2. Save to `.notes/` folder using the Write tool

3. Confirm save location to the user:
   ```
   Plan saved to: .notes/[filename].md
   ```

---

## Step 6: Run Background Agents Sequentially

Run three background agents to review and enhance the plan. Execute them **sequentially** (wait for each to complete before starting the next).

### 6a. Frontend Validator Review

```bash
cmd.exe //c "claude -p \"@.claude/agents/frontend-validator.md Read the plan at @.notes/[filename].md and review it against the frontend standards. Check for:
1. Proper component structure
2. Correct file naming conventions
3. TypeScript best practices
4. Accessibility considerations
5. State management patterns

If you find issues, update the plan file by MODIFYING the existing task descriptions to include the necessary notes and requirements. Do NOT add new sections - integrate your feedback directly into the task descriptions.\""
```

**Execution:**
1. Call Bash with `run_in_background: true`
2. Use TaskOutput with `block: true` to wait for completion
3. Show summary of changes made

### 6b. Security Scanner Review

```bash
cmd.exe //c "claude -p \"@.claude/agents/security-scanner.md Read the plan at @.notes/[filename].md and analyze it for security vulnerabilities. Check for:
1. Authentication/authorization issues
2. Input validation concerns
3. Data exposure risks
4. SQL injection possibilities
5. XSS vulnerabilities
6. Insecure data storage

If you find security concerns, update the plan file by MODIFYING the existing task descriptions to include the necessary security requirements. Do NOT add new sections - integrate security requirements directly into the relevant task descriptions (e.g., 'Implement form with input validation and XSS protection').\""
```

**Execution:**
1. Call Bash with `run_in_background: true`
2. Use TaskOutput with `block: true` to wait for completion
3. Show summary of security findings

### 6c. Playwright QA Analyst Review

```bash
cmd.exe //c "claude -p \"@.claude/agents/playwright-qa-analyst.md Read the plan at @.notes/[filename].md and generate comprehensive Playwright test scenarios. For each feature/phase, identify:
1. Happy path tests
2. Edge case tests
3. Error handling tests
4. Accessibility tests
5. Cross-browser considerations

Add a FINAL PHASE at the end of the Execution Strategy section called 'Phase N: E2E Testing' (where N is the next phase number). This phase should:
- Use **Agent:** \`playwright\`
- List each test scenario as a task in the same format as other phases
- Each task should be a specific, executable test (e.g., '- [ ] Test login form validates email format')
- These tasks are PART OF THE EXECUTION and will be run by run-plan-with-test.md\""
```

**Execution:**
1. Call Bash with `run_in_background: true`
2. Use TaskOutput with `block: true` to wait for completion
3. Show summary of test scenarios added

---

## Step 7: Display Final Plan

After all background agents complete:

1. **Read the final plan** from `.notes/[filename].md`
2. **Display the complete plan** to the user
3. **Summarize enhancements** made by each agent:
   ```
   Plan Enhanced!

   📁 Saved to: .notes/[filename].md

   Enhancements:
   ✅ Frontend Validator: [tasks enhanced with frontend requirements]
   ✅ Security Scanner: [tasks enhanced with security requirements]
   ✅ Playwright QA: [number] E2E test tasks added to final phase

   The plan is ready for execution with `/run-plan .notes/[filename].md`
   ```

---

## Error Handling

### If user description is unclear:
- Ask specific clarifying questions
- Do NOT proceed until requirements are clear

### If agent detection is ambiguous:
- Ask the user which areas are involved (frontend, backend, or both)

### If background agent fails:
- Report the error
- Ask user if they want to retry or proceed without that agent's review

### If plan file cannot be saved:
- Report the error
- Suggest alternative filename or location

