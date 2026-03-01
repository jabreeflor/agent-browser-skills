# Agent Browser Custom Skills

Custom skills for [agent-browser](https://github.com/vercel-labs/agent-browser) to automate Electron desktop apps.

## Available Skills

| Skill | App | Description |
|-------|-----|-------------|
| `spotify` | Spotify Desktop | Music playback, search, playlists, library |
| `teams` | Microsoft Teams | Messaging, meetings, channels, calls |
| `discord` | Discord Desktop | Messaging, voice channels, servers, DMs, threads |
| `bruno` | Bruno API Client | HTTP requests, collections, environments, testing |
| `figma` | Figma Desktop | Design creation - shapes, frames, text, components, auto layout, export |

## Installation

```bash
# Add Spotify skill
npx agent-browser skills add jabreeflor/agent-browser-skills --skill spotify

# Add Teams skill
npx agent-browser skills add jabreeflor/agent-browser-skills --skill teams

# Add Discord skill
npx agent-browser skills add jabreeflor/agent-browser-skills --skill discord

# Add Bruno skill
npx agent-browser skills add jabreeflor/agent-browser-skills --skill bruno

# Add Figma skill
npx agent-browser skills add jabreeflor/agent-browser-skills --skill figma
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

### Discord

```bash
# Connect to Discord (must be running)
agent-browser connect discord

# Messaging
agent-browser --skill discord send "Hello everyone!"
agent-browser --skill discord reply "I agree!"
agent-browser --skill discord open-dm "username"

# Voice
agent-browser --skill discord join-voice "General"
agent-browser --skill discord leave-voice
agent-browser --skill discord toggle-mute
agent-browser --skill discord toggle-deafen
agent-browser --skill discord share-screen

# Navigation
agent-browser --skill discord open-server "My Server"
agent-browser --skill discord open-channel "general"
agent-browser --skill discord go-home

# Search
agent-browser --skill discord search "keyword"
agent-browser --skill discord search-from "username"
agent-browser --skill discord search-mentions

# Friends
agent-browser --skill discord show-friends-online
agent-browser --skill discord add-friend "user#1234"

# Status
agent-browser --skill discord set-status "dnd"
agent-browser --skill discord set-custom-status "Coding..."
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

### Figma

```bash
# Connect to Figma (must be running)
agent-browser connect 9226

# Create shapes
agent-browser --skill figma create-rectangle 200 100
agent-browser --skill figma create-ellipse 50 50
agent-browser --skill figma create-frame 375 812

# Style elements
agent-browser --skill figma set-fill-color "#3B82F6"
agent-browser --skill figma set-corner-radius 8
agent-browser --skill figma set-opacity 0.9

# Typography
agent-browser --skill figma create-text "Hello World"
agent-browser --skill figma set-font-family "Inter"
agent-browser --skill figma set-font-size 16

# Layout
agent-browser --skill figma add-auto-layout
agent-browser --skill figma set-auto-layout-gap 12
agent-browser --skill figma set-auto-layout-padding 16

# Components
agent-browser --skill figma create-button-component "Sign Up" "#3B82F6"
agent-browser --skill figma create-card-layout 320 "User Profile"

# Export
agent-browser --skill figma export-as-png
agent-browser --skill figma export-as-svg
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
