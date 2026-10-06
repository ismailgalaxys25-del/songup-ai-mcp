# SongUp AI MCP Server

Official [Model Context Protocol](https://modelcontextprotocol.io) server for [SongUp AI](https://www.songupai.com), the AI song maker.
Connect it to Cursor, VS Code, Claude Code, Windsurf, Zapier, Make, n8n or any other MCP client to:

- **Find AI songs** from the SongUp AI library in 24 languages, by genre, mood or occasion, each with a direct link to its audio.
- **Start a custom song**: turn a song idea (occasion, names, story, mood) into a link that opens the SongUp AI song maker with the idea filled in.
- **Find an audio tool** for a task such as stem separation, vocal removal, mashups, noise removal, mastering, chords or audio-to-MIDI.

It is a hosted server: there is nothing to install, no sign-in and no API key.

| | |
|---|---|
| **URL** | `https://www.songupai.com/mcp/agents` |
| **Transport** | Streamable HTTP |
| **Authentication** | None |
| **Tools** | 3, all read-only |
| **Registry name** | `com.songupai/songup-ai` |
| **Docs** | https://www.songupai.com/mcp-server |

## Setup

### Cursor

`~/.cursor/mcp.json` (or `.cursor/mcp.json` in a project):

```json
{
  "mcpServers": {
    "songup-ai": { "url": "https://www.songupai.com/mcp/agents" }
  }
}
```

### VS Code (GitHub Copilot)

`.vscode/mcp.json`:

```json
{
  "servers": {
    "songup-ai": { "type": "http", "url": "https://www.songupai.com/mcp/agents" }
  }
}
```

### Claude Code

```bash
claude mcp add --transport http songup-ai https://www.songupai.com/mcp/agents
```

### Windsurf

`~/.codeium/windsurf/mcp_config.json`:

```json
{
  "mcpServers": {
    "songup-ai": { "serverUrl": "https://www.songupai.com/mcp/agents" }
  }
}
```

### Claude and ChatGPT

Use the in-chat versions, which play songs right in the conversation:

- Claude: add `https://www.songupai.com/mcp/claude` as a custom connector ([guide](https://www.songupai.com/claude-connector)).
- ChatGPT: the SongUp AI app ([guide](https://www.songupai.com/chatgpt-app)).

### Zapier, Make and n8n

- **Zapier:** add an **MCP Client** step, connect with the server URL, transport Streamable HTTP, no authentication.
- **Make:** add the **MCP Client** module, create a connection with the server URL and no authentication.
- **n8n:** give an **AI Agent** node the **MCP Client Tool**, set the endpoint to the server URL, transport HTTP Streamable, authentication None.

## Tools

| Tool | Input | Returns |
|---|---|---|
| `find_songs` | `language` (one of 24 song languages, or `Instrumental`), optional `query` (genre, mood or occasion), optional `limit` (1–10) | Songs from the SongUp AI library with title, genre, vocals, description and a direct audio link |
| `start_custom_song` | `idea` (up to 500 characters), optional `language` | A link that opens the SongUp AI song maker with the idea filled in |
| `find_audio_tool` | `task` (what you want to do with your audio) | Up to three SongUp AI browser tools with what each does and a link |

Library songs are ready-made examples, not made from your words. The tools never create songs, take payment or change anything;
custom songs are made on songupai.com with a SongUp AI account.

## Example prompts

- "Find three upbeat Spanish reggaeton songs on SongUp AI."
- "Play me some Arabic songs made with AI."
- "Start a birthday song for my friend Sara, who loves cats, in English."
- "Which SongUp AI tool removes vocals from a song?"

## Try it with curl

```bash
curl -s https://www.songupai.com/mcp/agents \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"find_songs","arguments":{"language":"Hindi","query":"lo-fi","limit":3}}}'
```

## Privacy and support

The server receives only the tool inputs your app sends. It does not store them or link them to a person, and sets no cookies.
See the [privacy policy](https://www.songupai.com/privacy#ai-apps).

Questions or problems: support@songupai.com or [songupai.com/contact](https://www.songupai.com/contact).

## About this repository

This repository holds the public listing (`server.json` for the [MCP Registry](https://registry.modelcontextprotocol.io)) and setup docs
for the hosted SongUp AI MCP server, under the MIT license. The server itself runs at songupai.com.
