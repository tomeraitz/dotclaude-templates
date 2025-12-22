# Debugger Skill

A skill that automatically verifies frontend changes using Playwright MCP.

## Setup

1. Install Playwright MCP server:
```bash
claude mcp add playwright npx @playwright/mcp@latest
```

## Usage

After completing any frontend task, invoke the debugger skill to verify your changes work correctly.

### Basic Flow

1. **Start server** - Ensure your frontend server is running (`npm start`)
2. **Navigate** - Open the page with your changes
3. **Interact** - Simulate user actions (clicks, typing, form submissions)
4. **Check console** - Look for errors or warnings
5. **Capture snapshot** - Verify the UI state

### Common Commands

| Action | Tool |
|--------|------|
| Open page | `browser_navigate` |
| Click element | `browser_click` |
| Type text | `browser_type` |
| Fill form | `browser_fill_form` |
| Check console | `browser_console_messages` |
| Get UI state | `browser_snapshot` |
| Take screenshot | `browser_take_screenshot` |

### Example

Testing a login form:
```
1. browser_navigate → http://localhost:<port>/login
2. browser_type → Enter email
3. browser_type → Enter password
4. browser_click → Submit button
5. browser_console_messages → Check for errors
6. browser_snapshot → Verify success state
```

## When to Use

- New component implementation
- Bug fixes
- UI modifications
- Form implementations
- Navigation changes

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Server not running | Run `npm start` |
| Console errors | Fix the error, re-run verification |
| Element not found | Check `browser_snapshot` for correct element refs |
