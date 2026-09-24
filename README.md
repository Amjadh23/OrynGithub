# jira-buddy

A Claude Code plugin for managing Jira tickets in plain English — create,
update, search, transition, comment on, and assign tickets — without leaving
the chat.

It works through Atlassian's official remote MCP server. There's no shared
account and no API key to hand out: each person connects their **own**
Atlassian account, and only ever sees what they already have Jira permission
for.

## Install

1. Clone this repo somewhere on your machine:
   ```bash
   git clone <this-repo-url> jira-buddy
   ```
2. In Claude Code, add it as a plugin:
   ```bash
   claude plugin add ./jira-buddy
   ```
   (or add this repo as a marketplace source if you're distributing it that
   way — see `claude plugin marketplace add`)
3. Start (or restart) a Claude Code session in any project.

## First use

The first time you ask Claude to do something Jira-related (e.g. "create a
Jira ticket for X"), Claude Code will prompt you to authenticate — this
opens a browser window for a normal Atlassian login/OAuth consent. After
that you're connected and it won't ask again.

You can also connect manually ahead of time:
```bash
claude mcp add --transport http atlassian https://mcp.atlassian.com/v2/mcp
```
then run `/mcp` in a session to trigger the login.

## What you can ask for

- "Create a bug ticket in KAN for the login page crashing on mobile"
- "Move KAN-123 to in progress"
- "What are my open tickets?"
- "Assign KAN-45 to Sarah"
- "Comment on KAN-12: fixed in the latest deploy"

If it's ever unclear which Jira site or project you mean, it'll ask instead
of guessing. Anything that changes data (create/update/transition/comment/
assign) gets a quick confirmation before it happens.

## Requirements

- Claude Code
- A Jira Cloud account with access to the site(s) you want to use
