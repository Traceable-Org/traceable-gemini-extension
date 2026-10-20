# Traceable for Gemini CLI

Connects Gemini CLI to [Traceable](https://traceabledocs.com), where regulated
product teams keep their requirements, risk assessments, test protocols and the
trace links between them. Gemini works in your Traceable account with your
permissions: it maps projects, reads documents, drafts new ones from your
templates, writes requirements into ID grids, creates trace links, records test
results and searches the Reference Library. Every change lands in a draft, and
publishing and e-signature stay with people.

This extension adds one remote MCP server, `https://app.traceabledocs.com/api/mcp/mcp`
(streamable HTTP). There is nothing to build and no key to paste: Gemini CLI
signs you in to Traceable with OAuth in your browser the first time it connects.

> Google no longer serves Gemini CLI to personal Google accounts (it points
> them to Antigravity). This extension is for Gemini CLI users on Gemini Code
> Assist Standard or Enterprise, or with a paid Gemini API key. Antigravity users
> add the server in Antigravity's MCP settings with `serverUrl` instead; see the
> Traceable MCP manual.

## Install

```bash
gemini extensions install https://github.com/Traceable-Org/traceable-gemini-extension
```

Restart Gemini CLI. If it does not open the browser by itself, run
`/mcp auth traceable`. Sign-in needs a local browser, so it does not work over
SSH without one.

To add the server without the extension, put this in `~/.gemini/settings.json`:

```json
{
  "mcpServers": {
    "traceable": { "httpUrl": "https://app.traceabledocs.com/api/mcp/mcp" }
  }
}
```

## Requirements

A Traceable account with MCP access enabled for you by an organisation admin
(Org settings > Members). Included on every Traceable plan, with rate limits on
Free.

## Links

- Documentation: https://traceabledocs.com/mcp
- Privacy policy: https://app.traceabledocs.com/legal/privacy
- Terms: https://app.traceabledocs.com/legal/eula
- Support: info@traceabledocs.com

## Layout

`gemini-extension.json` at the root is the whole extension. It is maintained in
the Traceable monorepo under `integrations/gemini/` and mirrored to the public
repository the Gemini CLI gallery indexes (topic `gemini-cli-extension`); keep
`version` in step with the MCP server version in `server.json`.
