# Spotify Skill

Control Spotify Desktop app with agent-browser.

## Requirements

- Spotify Desktop app installed
- Spotify running with remote debugging enabled:
  ```bash
  # macOS
  open -a Spotify --args --remote-debugging-port=9222
  
  # Windows
  spotify.exe --remote-debugging-port=9222
  
  # Linux
  spotify --remote-debugging-port=9222
  ```

## Quick Start

```bash
# Connect to running Spotify
agent-browser connect 9222

# Play/pause
agent-browser --skill spotify toggle

# Search and play
agent-browser --skill spotify search "Kendrick Lamar"
agent-browser --skill spotify play-track "HUMBLE."

# Get what's playing
agent-browser --skill spotify get-now-playing
```

## Commands

### Playback
| Command | Description |
|---------|-------------|
| `play` | Resume playback |
| `pause` | Pause playback |
| `toggle` | Toggle play/pause |
| `next` | Skip to next track |
| `previous` | Go to previous track |
| `shuffle` | Toggle shuffle |
| `repeat` | Cycle repeat mode |
| `mute` | Toggle mute |

### Search & Play
| Command | Params | Description |
|---------|--------|-------------|
| `search` | `query` | Search for music |
| `play-track` | `trackName` | Search and play a track |

### Library
| Command | Description |
|---------|-------------|
| `like` | Like current track |
| `add-to-queue` | Add to play queue |

### Navigation
| Command | Description |
|---------|-------------|
| `go-home` | Go to Home |
| `go-library` | Go to Your Library |
| `open-queue` | Open play queue |

### Info
| Command | Returns | Description |
|---------|---------|-------------|
| `get-now-playing` | `trackName`, `artistName` | Get current track info |

## Examples

```bash
# Play a specific artist
agent-browser --skill spotify search "The Weeknd"
agent-browser click "@e3"  # Click first artist result

# Create a listening session
agent-browser --skill spotify go-library
agent-browser --skill spotify shuffle
agent-browser --skill spotify play

# Queue management
agent-browser --skill spotify add-to-queue
agent-browser --skill spotify open-queue
```

## Troubleshooting

**Can't connect to Spotify?**
- Make sure Spotify is running with `--remote-debugging-port=9222`
- Check if port 9222 is available: `lsof -i :9222`

**Selectors not working?**
- Spotify updates may change the UI structure
- Run `agent-browser snapshot` to see current element refs
- Submit an issue or PR to update selectors
