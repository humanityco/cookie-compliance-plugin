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

Cursor: install from [cursor.com/marketplace](https://cursor.com/marketplace) once listed (search for **Cookie Compliance**). Until then, test locally or add the MCP server manually.

**Local plugin test (recommended before marketplace review):** clone this repo and symlink or copy it into `%USERPROFILE%\.cursor\plugins\local\cookie-compliance` (macOS/Linux: `~/.cursor/plugins/local/cookie-compliance`). Reload Cursor, open **Customize → Plugins**, and enable the local plugin. Sign in through the browser when prompted for the `cookie-compliance` MCP server.

**Manual MCP (no plugin bundle):** add this to `.cursor/mcp.json` for one project or `~/.cursor/mcp.json` for all projects:

```json
{"mcpServers": {"cookie-compliance": {"url": "https://mcp.cookie-compliance.co/mcp/account"}}}
```

Then sign in through the browser when prompted.

Claude (claude.ai and Claude Desktop): Customize, then Connectors, then Add custom connector. Name it `Cookie Compliance`, paste `https://mcp.cookie-compliance.co/mcp/account`, choose Sign in now and Register automatically, then approve in the browser.

If browser sign-in is not possible, an Admin or Super Admin can create an API token in the Cookie Compliance dashboard (labelled Temporary Login). Add it to your MCP client as a bearer token in the `Authorization` header, using the client's own secret or environment-variable settings. Do not paste a token into a chat, and do not save it in a file you commit. Tokens expire.

## Try it without an account

Use `https://mcp.cookie-compliance.co/mcp` instead. It gives you the anonymous install, demo and help tools, and a preview banner that cannot change a live one.

## Verify

Ask your assistant "Which Cookie Compliance sites can you see?" If it cannot list your sites, check that you used the account address and that your token has not expired.

## Publish to the Cursor marketplace

This repo is the source for the official listing. Maintainers: after changes are on `main`, submit or request re-index at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish) with:

`https://github.com/humanityco/cookie-compliance-plugin`

Listings are manually reviewed (security, quality, open source). There is no public status page; Cursor follows up by email. See the [Plugins reference](https://cursor.com/docs/reference/plugins) and [Publisher Terms](https://cursor.com/marketplace-publisher-terms).

## Links

Website: https://cookie-compliance.co/
Connect guide: https://manual.hu-manity.co/connect/
Agent manual: https://manual.hu-manity.co/

## Support

Email support@hu-manity.co.

## Licence

ISC. See the repository for the full licence text.
