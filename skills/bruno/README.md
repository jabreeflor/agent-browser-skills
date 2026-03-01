# Bruno Skill

Control [Bruno](https://www.usebruno.com/) API client with agent-browser.

## Why Bruno?

- 🗂️ **Git-friendly** — Collections stored as files, not cloud
- ⚡ **Fast** — Lightweight Electron app
- 🔒 **Offline** — No account required
- 🆓 **Open source** — MIT licensed

## Requirements

- Bruno installed: https://www.usebruno.com/downloads
- Launch with remote debugging:
  ```bash
  # macOS
  open -a Bruno --args --remote-debugging-port=9224
  
  # Windows
  bruno.exe --remote-debugging-port=9224
  
  # Linux
  bruno --remote-debugging-port=9224
  ```

## Quick Start

```bash
# Connect to running Bruno
agent-browser connect 9224

# Make a GET request
agent-browser --skill bruno set-method GET
agent-browser --skill bruno set-url "https://api.github.com/users/jabreeflor"
agent-browser --skill bruno send

# Or in one command
agent-browser --skill bruno request GET "https://httpbin.org/get"

# Get response
agent-browser --skill bruno get-response-status
agent-browser --skill bruno get-response-body
```

## Commands

### Requests
| Command | Params | Description |
|---------|--------|-------------|
| `send` | - | Send current request |
| `save` | - | Save current request |
| `set-method` | `method` | Set HTTP method (GET, POST, PUT, DELETE, PATCH) |
| `set-url` | `url` | Set request URL |
| `request` | `method`, `url` | Set method + URL and send |
| `new-request` | - | Create new request |

### Request Configuration
| Command | Params | Description |
|---------|--------|-------------|
| `add-header` | `key`, `value` | Add request header |
| `add-param` | `key`, `value` | Add query parameter |
| `set-body-json` | `json` | Set JSON body |
| `set-bearer-token` | `token` | Set Bearer auth |

### Tabs
| Command | Description |
|---------|-------------|
| `tab-params` | Go to Params tab |
| `tab-headers` | Go to Headers tab |
| `tab-body` | Go to Body tab |
| `tab-auth` | Go to Auth tab |
| `tab-tests` | Go to Tests tab |

### Collections
| Command | Description |
|---------|-------------|
| `new-collection` | Create collection |
| `import-collection` | Import collection |
| `search` | Search requests |
| `run-collection` | Run all requests |

### Response
| Command | Returns | Description |
|---------|---------|-------------|
| `get-response-status` | `status` | Get status code |
| `get-response-time` | `time` | Get response time |
| `get-response-body` | `body` | Get response body |
| `copy-response` | - | Copy to clipboard |

### Environment
| Command | Params | Description |
|---------|--------|-------------|
| `set-environment` | `envName` | Select environment |

## Examples

```bash
# API testing workflow
agent-browser --skill bruno new-request
agent-browser --skill bruno set-method POST
agent-browser --skill bruno set-url "https://api.example.com/users"
agent-browser --skill bruno add-header "Content-Type" "application/json"
agent-browser --skill bruno set-body-json '{"name": "Test", "email": "test@example.com"}'
agent-browser --skill bruno set-bearer-token "your-token-here"
agent-browser --skill bruno send
agent-browser --skill bruno get-response-status

# Switch environments
agent-browser --skill bruno set-environment "production"
agent-browser --skill bruno send

# Run collection tests
agent-browser --skill bruno run-collection
```

## Integration with Claude Code

Bruno stores collections as `.bru` files — Claude can:
1. Read/write `.bru` files directly
2. Use this skill to execute requests
3. Parse responses for testing

```bash
# Claude reads the collection
cat my-api/users/create.bru

# Executes via agent-browser
agent-browser --skill bruno request POST "{{baseUrl}}/users"

# Gets response for validation
agent-browser --skill bruno get-response-body
```

## Troubleshooting

**Can't connect?**
- Ensure Bruno is running with `--remote-debugging-port=9224`
- Check port: `lsof -i :9224`

**Selectors not working?**
- Bruno updates may change UI
- Run `agent-browser snapshot` to inspect
- Submit PR with updated selectors
