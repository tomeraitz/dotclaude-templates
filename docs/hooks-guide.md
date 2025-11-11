# Claude Code Hooks Guide

## Overview

Hooks in `.claude/settings.json` are powerful automation mechanisms that allow you to execute commands or inject context in response to specific events in Claude Code. They enable you to customize Claude's behavior and ensure consistent workflows.

## The UserPromptSubmit Hook

### What It Does

The `UserPromptSubmit` hook executes automatically **every time you submit a prompt** to Claude. In this configuration, it injects additional context before Claude processes your request.

```json
{
  "hooks": {
    "UserPromptSubmit": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "echo '{\"additionalContext\": \"Before starting any task, ask clarifying questions to ensure you fully understand the requirements. Do not make assumptions.\"}'"
          }
        ]
      }
    ]
  }
}
```

### How It Works

1. **Trigger**: Activated when you press Enter/Submit on any prompt
2. **Execution**: Runs the specified command (`echo` with JSON payload)
3. **Injection**: The `additionalContext` is automatically added to Claude's context
4. **Result**: Claude receives your prompt + the additional instruction

### Why It's Important

#### 1. **Enforces Best Practices**
- Prevents Claude from making assumptions
- Ensures thorough requirement gathering
- Reduces back-and-forth corrections

#### 2. **Consistency Across Sessions**
- Every interaction follows the same clarification-first approach
- No need to manually remind Claude to ask questions
- Standardizes the development workflow

#### 3. **Saves Time**
- Catches ambiguities early in the process
- Prevents wasted work on incorrect implementations
- Reduces debugging and rework

#### 4. **Project-Specific Behavior**
- Can be customized per project in `.claude/settings.json`
- Different projects can enforce different workflows
- Team members get consistent Claude behavior

### Example Use Case

**Without the Hook:**
```
User: "Add a login feature"
Claude: *immediately starts coding a login system with assumptions*
```

**With the Hook:**
```
User: "Add a login feature"
Claude: "Before I start, let me clarify a few things:
- What authentication method? (email/password, OAuth, SSO?)
- Should it include registration functionality?
- Do you need password reset capability?
- Any specific security requirements?"
```

## Other Hook Types

While this configuration uses `UserPromptSubmit`, Claude Code supports other hook types:

- **ToolCall**: Execute commands when specific tools are invoked
- **PreCommit**: Run checks before git commits
- **Custom Events**: Project-specific automation triggers

## Customization Tips

### Adding Multiple Instructions

```json
{
  "additionalContext": "Before starting: 1) Ask clarifying questions 2) Review existing code 3) Propose architecture"
}
```

### Running Scripts Instead of Echo

```json
{
  "type": "command",
  "command": "node .claude/scripts/inject-context.js"
}
```

### Conditional Hook Execution

You can create scripts that conditionally inject context based on:
- Time of day
- Current git branch
- File types in the project
- Environment variables

## Best Practices

1. **Keep Instructions Clear**: Make the additional context concise and actionable
2. **Test Your Hooks**: Verify they execute correctly with simple prompts
3. **Document Your Hooks**: Explain why each hook exists (like this document!)
4. **Version Control**: Commit `.claude/settings.json` so team members benefit
5. **Avoid Over-Automation**: Too many hooks can slow down interactions

## Troubleshooting

### Hook Not Executing?
- Check JSON syntax in `settings.json`
- Verify the command works in your terminal
- Look for error messages in Claude Code output

### Hook Slowing Down Responses?
- Optimize the command execution time
- Consider using simpler echo statements instead of scripts
- Remove unnecessary hooks

## Security Considerations

- **Validate Commands**: Ensure hooks don't execute untrusted code
- **Review Echo Output**: Check that injected context doesn't leak sensitive data
- **Team Alignment**: Document all hooks for team transparency

## Conclusion

The `UserPromptSubmit` hook is a simple yet powerful feature that ensures Claude Code always starts tasks with the right approach. By forcing clarification before action, it prevents common pitfalls and leads to better, more accurate implementations.
