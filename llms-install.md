# Installing the SongUp AI MCP server

SongUp AI is a hosted remote MCP server. There is nothing to download, build or install, no API key and no environment variables.

- URL: `https://www.songupai.com/mcp/agents`
- Transport: Streamable HTTP
- Authentication: none

## Cline

Add this entry to `cline_mcp_settings.json`:

```json
{
  "mcpServers": {
    "songup-ai": {
      "type": "streamableHttp",
      "url": "https://www.songupai.com/mcp/agents",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

Save the file. Cline connects and lists three read-only tools:

- `find_songs`: ready-made AI songs from the SongUp AI library, by language, genre, mood or occasion, each with a direct MP3 link.
- `start_custom_song`: turns a song idea into a link that opens the SongUp AI song maker with the idea filled in.
- `find_audio_tool`: finds the right SongUp AI audio tool for a task (stem separation, vocal removal, mastering, chords, audio-to-MIDI and more).

## Check it works

Ask Cline: "Find an upbeat English birthday song on SongUp AI." It should call `find_songs` and return songs with audio links.
