---
name: jira-buddy
description: Use when the user asks to create a Jira ticket/issue, update or edit one, search or list tickets, move/transition a ticket's status, comment on a ticket, or assign/reassign a ticket. Works through the Atlassian remote MCP connector (tools prefixed like "mcp__atlassian__...").
---

# Jira Buddy

Helps create, update, search, and manage Jira tickets through Atlassian's
official remote MCP server. Each user authenticates their own Atlassian
account (OAuth) the first time they use it — you only ever see tickets and
projects that user already has permission for.

## Before the first action in a session

If no Atlassian site has been established yet, call the resource/site
discovery tool (e.g. `getAccessibleAtlassianResources` or equivalent) to find
which Jira Cloud site(s) the user's account has access to.

- If there's exactly one site, use it silently.
- If there's more than one, ask which site to use — don't guess.

If the user hasn't connected yet, calling any Atlassian tool will prompt
Claude Code's OAuth flow automatically — just proceed, no special handling
needed.

## General rules

- **This skill is generic** — never assume a specific Jira site or project.
  If the user doesn't name a project and it isn't obvious from recent
  conversation, ask for the project key (or ask them to pick from the site's
  visible projects).
- **Read actions run freely**: searching, listing, and looking up ticket
  details need no confirmation.
- **Mutating actions need a one-line confirmation** before you call the
  tool: creating, updating, transitioning, commenting, and assigning. State
  what you're about to do (site, project, ticket key if applicable, the
  change) and wait for a yes. This mirrors the "explicit permission for
  side-effectful actions" rule Claude already follows generally — don't skip
  it just because the user sounds casual.
- **Translate friendly language into Jira fields.** Users won't know field
  names or exact status strings — you resolve them:
  - "move it to in progress" / "mark it done" → look up the issue's
    available transitions and pick the matching one; if none matches
    closely, show the available options and ask.
  - "assign it to me" → resolve to the current user's account.
  - "assign it to <name>" → look up/search for the matching account; if
    ambiguous, list candidates and ask.
  - bug/task/story type, priority, labels — infer from wording when clearly
    stated ("this is a bug", "high priority"), otherwise leave unset rather
    than guessing.

## Actions

### Create a ticket
1. Confirm site + project (see above).
2. Gather: summary (required), description, issue type, priority, labels,
   assignee — only what the user gave or clearly implied. Don't interrogate
   for optional fields; a bare "create a ticket for X" is enough to proceed
   with sensible defaults (issue type "Task" unless the wording implies
   otherwise, e.g. "bug").
3. Confirm the summary line, then create it.
4. Report back the new ticket's key and a link.

### Update an existing ticket
1. Resolve the ticket by key (e.g. `KAN-123`) if given, or by searching if
   the user describes it (title, "the ticket I made yesterday about X",
   etc.) — confirm the match if there's any ambiguity.
2. Confirm the specific field changes, then apply them.

### Search / list tickets
Translate the request into JQL (or the structured search parameters the
tool accepts) — e.g. "my open tickets in KAN" → project = KAN AND
assignee = currentUser() AND status != Done. Show results as a compact
list: key, summary, status, assignee. No confirmation needed.

### Transition status
Look up the ticket's current status and available transitions before
picking one — don't assume every project uses the same workflow names.

### Comment
Confirm the ticket and the comment text, then post it.

### Assign / reassign
Resolve the target person to an account ID (via lookup/search), confirm,
then apply.

## Error handling

If a tool call fails (permission denied, invalid transition, unknown
project, etc.), surface the actual error to the user rather than retrying
blindly or guessing a workaround — Jira permissions and workflows vary a lot
per site and this skill can't know them in advance.
