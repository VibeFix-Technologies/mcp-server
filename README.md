# @vibefix/mcp

Your AI built it. It broke. Post the bug, a real developer fixes it.

[VibeFix](https://vibefix.co) is a bug bounty platform for vibe coders. This MCP server lets you browse bounties, post bugs, submit fixes, and run website diagnostics directly from Claude Code, Cursor, Windsurf, or any MCP-compatible client. Free to post.

## Setup

### 1. Get an API key

Sign in to VibeFix as a developer → **Dashboard → MCP / API** → Generate Key.

### 2. Add to your MCP client

**Claude Code** (`~/.claude.json`):

```json
{
  "mcpServers": {
    "vibefix": {
      "command": "npx",
      "args": ["@vibefix/mcp"],
      "env": {
        "VIBEFIX_API_KEY": "vf_your_key_here"
      }
    }
  }
}
```

**Claude Desktop** (`claude_desktop_config.json`) — same config above.

**Cursor / Windsurf** — go to Settings → MCP Servers and paste the same JSON.

### 3. Start using it

Ask your AI assistant:

> *"List open VibeFix bounties for deployment bugs"*
> *"Show me the full details for job j57..."*
> *"Submit my fix for job j57... — here's what I changed: ..."*

---

## Available tools

### For developers

| Tool | Description |
|------|-------------|
| `vibefix_list_bounties` | Browse open bounties — filter by `category`, `platform`, `difficulty` |
| `vibefix_get_bounty` | Full bounty details: description, expected vs actual behavior, stack |
| `vibefix_my_profile` | Your XP, level, wallet balance, and approval status |
| `vibefix_my_submissions` | Your submitted fixes with acceptance status |
| `vibefix_my_applications` | Your applications to private bounties with approval status |
| `vibefix_apply_to_bounty` | Apply to a private bounty with an intro message |
| `vibefix_submit_solution` | Submit your fix with a description and repo link |

### For customers

| Tool | Description |
|------|-------------|
| `vibefix_post_bounty` | Post a new bounty — free goes live instantly, paid returns checkout URL |
| `vibefix_my_bounties` | List your posted bounties with status and submission counts |
| `vibefix_list_submissions` | See all submissions received for one of your bounties |
| `vibefix_accept_submission` | Accept a winning fix — awards payout and XP to the developer |

### Diagnostics

| Tool | Description |
|------|-------------|
| `vibefix_diagnose` | Run a Lighthouse audit + JS error scan on any URL — returns performance, SEO, and bug report |

### Filters for `vibefix_list_bounties`

- **category**: `deployment` `auth` `payments` `bug_fix` `performance` `other`
- **platform**: `cursor` `bolt` `lovable` `replit` `v0` `other`
- **difficulty**: `easy` `medium` `hard`

---

## Environment variables

| Variable | Required | Default | Description |
|----------|----------|---------|-------------|
| `VIBEFIX_API_KEY` | Yes | — | Your API key from vibefix.co/dashboard/mcp |
| `VIBEFIX_URL` | No | `https://vibefix.co` | Override for self-hosted instances |

---

## How it works

The MCP server connects to the VibeFix API at `vibefix.co/api/mcp/v1`. Your API key authenticates write operations (apply, submit). Browsing open jobs requires no key.

---

## License

MIT
