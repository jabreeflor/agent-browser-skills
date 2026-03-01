# Discord Skill

Control the Discord Desktop app via agent-browser.

## Requirements

- Discord Desktop must be running
- Launch with `--remote-debugging-port=9225` for Electron CDP access

## Capabilities

- **Messaging** - Send messages, reply, react, create threads
- **Voice** - Join/leave voice channels, mute, deafen, screen share, video
- **Servers** - Navigate servers, open channels, invite people
- **DMs** - Open and send direct messages
- **Friends** - View friends list, send friend requests
- **Search** - Search messages, filter by user, find mentions
- **Status** - Set online/idle/DND/invisible, custom status

## Usage

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

# Other
agent-browser --skill discord add-reaction "thumbsup"
agent-browser --skill discord create-thread "Discussion"
agent-browser --skill discord open-threads
agent-browser --skill discord open-pinned
agent-browser --skill discord open-inbox
```
