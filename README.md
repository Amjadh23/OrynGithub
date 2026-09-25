# OrynLab plugins

A Claude Code plugin marketplace with two plugins: **jira-buddy** and
**orynlab-skills**.

Add the marketplace once, then install whichever you want:

```bash
claude plugin marketplace add https://github.com/Amjadh23/OrynGithub.git
claude plugin install jira-buddy@jira-buddy
claude plugin install orynlab-skills@jira-buddy
```

---

## orynlab-skills

OrynLab's brand system, so anything carrying the name looks like it came from
the same place — decks, documents, social graphics, posters, business cards,
diagrams, README headers.

It covers the monochrome palette (no accent colour, by design), the geometric
type scale and its wide-tracked caps, the three-dot mark and wordmark rules,
and the curve-and-chevron shape language. Ships drop-in CSS custom properties
in `references/tokens.css` and the mark as SVG.

Use it by asking for something "in the OrynLab brand", or run
`/orynlab-skills` directly.

> The logo lockup itself is not in the repo yet — drop the SVG into
> `plugins/orynlab-skills/skills/orynlab-skills/assets/` and push. See that
> folder's README for the filenames it expects.

---

## jira-buddy

A Claude Code plugin for managing Jira tickets in plain English — create,
update, search, transition, comment on, and assign tickets — without leaving
the chat.

It works through Atlassian's official remote MCP server. There's no shared
account and no API key to hand out: each person connects their **own**
Atlassian account, and only ever sees what they already have Jira permission
for.

### Install

```bash
claude plugin install jira-buddy@jira-buddy
```

Then start (or restart) a Claude Code session in any project — plugins install
at the user level, so they're available everywhere, not just in one project.

## First use

The first time you ask Claude to do something Jira-related (e.g. "create a
Jira ticket for X"), Claude Code will prompt you to authenticate — this
opens a browser window for a normal Atlassian login/OAuth consent. After
that you're connected and it won't ask again.

You can also trigger the login ahead of time by running `/mcp` in a session
and picking `atlassian`.

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
