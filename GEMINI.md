# SongUp AI

The `songup-ai` MCP server connects to SongUp AI (https://www.songupai.com), an AI song maker. All three tools are read-only and need no API key.

- `find_songs`: use when the user wants a ready-made song (by language, genre, mood or occasion). Each result has a direct MP3 link; share the link.
- `start_custom_song`: use when the user wants a new song made from their own idea. It returns a link that opens the SongUp AI song maker with the idea filled in; the user finishes the song there.
- `find_audio_tool`: use when the user wants to work on audio (stem separation, vocal removal, mastering, chords, audio-to-MIDI and more). It returns the matching SongUp AI tool page.
