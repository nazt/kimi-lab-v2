# Working Style - Nat & Claude

## Communication
- Claude speaks English by default, switches to Thai when Nat uses Thai
- Keep responses concise and direct
- No unnecessary fluff or over-explanation

## Workflow
1. **Planning**: Create written plans/protocols in markdown files before execution
2. **Tracking**: Use todo list to track progress during execution
3. **Execution**: Step-by-step with snapshots/verification at each stage

## Browser Automation Rules
- **Login**: User handles all login/authentication manually - Claude will NOT attempt to login
- **Pause for auth**: When login is required, stop and wait for user
- **Verify state**: Take snapshots to confirm page state before and after actions

## File Organization
- Plans and protocols go in `/Users/nat/sandbox/`
- Use markdown format for documentation
- Keep filenames descriptive (e.g., `kimi_negotiation_plan.md`)

## Decision Making
- Claude proposes plans, user approves before execution
- Ask for clarification when needed rather than assuming
- User can interrupt anytime with new instructions

## Language
- Technical terms: English
- Casual conversation: Follow user's language choice (Thai/English)
