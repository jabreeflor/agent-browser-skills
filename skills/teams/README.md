# Microsoft Teams Skill

Control Microsoft Teams with agent-browser.

## Requirements

- Microsoft Teams desktop app installed
- Teams running with remote debugging enabled:
  ```bash
  # macOS
  open -a "Microsoft Teams" --args --remote-debugging-port=9223
  
  # Windows
  "C:\Users\%USERNAME%\AppData\Local\Microsoft\Teams\current\Teams.exe" --remote-debugging-port=9223
  
  # Linux
  teams --remote-debugging-port=9223
  ```

## Quick Start

```bash
# Connect to running Teams
agent-browser connect 9223

# Send a message
agent-browser --skill teams open-chat "John Doe"
agent-browser --skill teams send "Hey, quick question!"

# Join a meeting
agent-browser --skill teams go-calendar
agent-browser --skill teams join-meeting

# Control meeting
agent-browser --skill teams mute
agent-browser --skill teams toggle-video
```

## Commands

### Navigation
| Command | Description |
|---------|-------------|
| `go-activity` | Go to Activity feed |
| `go-chat` | Go to Chat |
| `go-teams` | Go to Teams |
| `go-calendar` | Go to Calendar |
| `go-calls` | Go to Calls |
| `go-files` | Go to Files |

### Messaging
| Command | Params | Description |
|---------|--------|-------------|
| `open-chat` | `personName` | Open chat with person |
| `send` | `message` | Send message in current chat |
| `open-channel` | `channelName` | Open a channel |
| `search` | `query` | Search Teams |

### Meetings
| Command | Description |
|---------|-------------|
| `join-meeting` | Join active meeting |
| `leave-meeting` | Leave current meeting |
| `mute` | Mute microphone |
| `unmute` | Unmute microphone |
| `toggle-mute` | Toggle mute |
| `toggle-video` | Toggle camera |
| `share-screen` | Open share menu |
| `raise-hand` | Raise hand |
| `open-meeting-chat` | Open meeting chat |
| `show-participants` | Show participants |
| `meet-now` | Start instant meeting |

### Status
| Command | Params | Description |
|---------|--------|-------------|
| `set-status` | `status` | Set status (available, busy, doNotDisturb, away) |
| `get-status` | - | Get current status |
| `get-unread` | - | Get unread count |

## Examples

```bash
# Morning routine
agent-browser --skill teams go-activity
agent-browser --skill teams get-unread

# Quick meeting join
agent-browser --skill teams go-calendar
# Click on meeting in calendar view
agent-browser click "@e5"
agent-browser --skill teams join-meeting

# Focus mode
agent-browser --skill teams set-status "doNotDisturb"

# End of day
agent-browser --skill teams set-status "away"
agent-browser --skill teams leave-meeting
```

## Troubleshooting

**Can't connect to Teams?**
- Make sure Teams is running with `--remote-debugging-port=9223`
- Check if port 9223 is available: `lsof -i :9223`
- New Teams app uses different process name than classic Teams

**Meeting controls not working?**
- Must be in an active meeting for meeting controls to appear
- Some controls only appear on hover - try `agent-browser hover` first

**Selectors not working?**
- Teams updates frequently and may change UI structure
- Run `agent-browser snapshot` to inspect current elements
- Submit an issue or PR to update selectors
