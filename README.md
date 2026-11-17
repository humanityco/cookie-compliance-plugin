# Cookie Compliance plugin

Cookie Compliance adds a cookie consent banner that blocks trackers until the visitor chooses, and records proof of consent. This plugin connects your AI assistant to the Cookie Compliance MCP server so it can install the banner, configure regions, preview changes and manage a live banner on your account.

## What you get

The plugin connects one MCP server, `https://mcp.cookie-compliance.co/mcp/account`. It exposes two kinds of tools.

Anonymous tools need no account. They cover `install.*` (the live embed snippet and placement rules for a registered app), `demo.*` (a preview-only banner) and `help.*` (signup, token setup and the settings reference).

Account tools need a Cookie Compliance account. They cover `account.*`: list and create apps, read and preview design and compliance changes, apply changes after review, check consent summaries and explain what the banner does per country or state.

Writes to a live banner go through a preview first. The server only applies a change that matches the reviewed preview.

## Install

Claude Code:

```
claude plugin marketplace add humanityco/cookie-compliance-plugin
claude plugin install cookie-compliance@cookie-compliance
```

Then start a session, run `/mcp`, select `cookie-compliance`, choose Authenticate and approve in the browser that opens. You never give your password to the assistant.

Cursor: once the plugin is listed in the Cursor marketplace, install it from there. Until then, add this to `.cursor/mcp.json` for one project or `~/.cursor/mcp.json` for all projects:

```json
{"mcpServers": {"cookie-compliance": {"url": "https://mcp.cookie-compliance.co/mcp/account"}}}
```

Then sign in through the browser when prompted.

Claude (claude.ai and Claude Desktop): Customize, then Connectors, then Add custom connector. Name it `Cookie Compliance`, paste `https://mcp.cookie-compliance.co/mcp/account`, choose Sign in now and Register automatically, then approve in the browser.

If sign-in is not possible, create an API token in the Cookie Compliance dashboard (labelled Temporary Login) as an Admin or Super Admin, and send it as an `Authorization: Bearer hu_...` header. Never paste a token into a chat. Tokens expire.

## Try it without an account

Use `https://mcp.cookie-compliance.co/mcp` instead. It gives you the anonymous install, demo and help tools, and a preview banner that cannot change a live one.

## Verify

Ask your assistant "Which Cookie Compliance sites can you see?" If it cannot list your sites, check that you used the account address and that your token has not expired.

## Links

Website: https://cookie-compliance.co/
Connect guide: https://manual.hu-manity.co/connect/
Agent manual: https://manual.hu-manity.co/

## Support

Email support@hu-manity.co.

## Licence

ISC. See the repository for the full licence text.
