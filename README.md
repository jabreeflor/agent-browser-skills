# Agent Browser Custom Skills

Custom skills for [agent-browser](https://github.com/vercel-labs/agent-browser) to automate Electron desktop apps.

## Available Skills

| Skill | App | Description |
|-------|-----|-------------|
| `spotify` | Spotify Desktop | Music playback, search, playlists, library |
| `teams` | Microsoft Teams | Messaging, meetings, channels, calls |
| `bruno` | Bruno API Client | HTTP requests, collections, environments, testing |

## Installation

```bash
# Add Spotify skill
npx agent-browser skills add jabreeflor/agent-browser-skills --skill spotify

# Add Teams skill
npx agent-browser skills add jabreeflor/agent-browser-skills --skill teams

# Add Bruno skill
npx agent-browser skills add jabreeflor/agent-browser-skills --skill bruno
```

## Usage

### Spotify

```bash
# Connect to Spotify (must be running)
agent-browser connect spotify

# Playback controls
agent-browser --skill spotify play
agent-browser --skill spotify pause
agent-browser --skill spotify next
agent-browser --skill spotify previous
agent-browser --skill spotify shuffle

# Search and play
agent-browser --skill spotify search "Drake"
agent-browser --skill spotify play-track "God's Plan"

# Get current state
agent-browser --skill spotify get now-playing
agent-browser --skill spotify get volume

# Playlist actions
agent-browser --skill spotify like
agent-browser --skill spotify add-to-playlist "Favorites"
```

### Microsoft Teams

```bash
# Connect to Teams (must be running)
agent-browser connect teams

# Messaging
agent-browser --skill teams open-chat "John Doe"
agent-browser --skill teams send "Hello!"
agent-browser --skill teams open-channel "General"

# Meetings
agent-browser --skill teams join-meeting
agent-browser --skill teams leave-meeting
agent-browser --skill teams mute
agent-browser --skill teams unmute
agent-browser --skill teams toggle-video

# Navigation
agent-browser --skill teams go activity
agent-browser --skill teams go chat
agent-browser --skill teams go teams
agent-browser --skill teams go calendar

# Get state
agent-browser --skill teams get unread
agent-browser --skill teams get status
```

### Bruno

```bash
# Connect to Bruno (must be running)
agent-browser connect 9224

# Make requests
agent-browser --skill bruno request GET "https://api.github.com/users/octocat"
agent-browser --skill bruno request POST "https://httpbin.org/post"

# Configure request
agent-browser --skill bruno add-header "Authorization" "Bearer token123"
agent-browser --skill bruno set-body-json '{"name": "test"}'
agent-browser --skill bruno send

# Get response
agent-browser --skill bruno get-response-status
agent-browser --skill bruno get-response-body

# Collections
agent-browser --skill bruno set-environment "production"
agent-browser --skill bruno run-collection
```

## Skill Structure

Each skill contains:
- `skill.json` - Metadata and configuration
- `selectors.json` - DOM selectors for UI elements
- `actions.json` - Pre-defined action workflows
- `README.md` - Skill-specific documentation

## Creating Custom Skills

1. Fork this repo
2. Create a new folder in `skills/`
3. Add the required JSON files
4. Test with `agent-browser --skill ./skills/yourskill`
5. Submit a PR!

## Requirements

- [agent-browser](https://github.com/vercel-labs/agent-browser) installed
- Target app must be running
- macOS, Windows, or Linux with desktop environment

## License

MIT
