# Figma Skill

Design creation in Figma Desktop app with agent-browser.

## Requirements

- Figma Desktop app installed
- Figma running with remote debugging enabled:
  ```bash
  # macOS
  open -a Figma --args --remote-debugging-port=9226

  # Windows
  figma.exe --remote-debugging-port=9226

  # Linux
  figma --remote-debugging-port=9226
  ```

## Quick Start

```bash
# Connect to running Figma
agent-browser connect 9226

# Select the rectangle tool and create a shape
agent-browser --skill figma tool-rectangle
agent-browser --skill figma create-rectangle --x 100 --y 100 --width 200 --height 150

# Set fill color
agent-browser --skill figma set-fill-color "#3B82F6"

# Add text
agent-browser --skill figma create-text --x 120 --y 140 --content "Hello World"
agent-browser --skill figma set-font-size 24
```

## Commands

### Tool Selection
| Command | Description |
|---------|-------------|
| `tool-move` | Switch to Move tool (V) |
| `tool-frame` | Switch to Frame tool (F) |
| `tool-rectangle` | Switch to Rectangle tool (R) |
| `tool-ellipse` | Switch to Ellipse tool (O) |
| `tool-line` | Switch to Line tool (L) |
| `tool-pen` | Switch to Pen tool (P) |
| `tool-text` | Switch to Text tool (T) |
| `tool-hand` | Switch to Hand tool (H) |

### Shape Creation
| Command | Params | Description |
|---------|--------|-------------|
| `create-rectangle` | `x`, `y`, `width`, `height` | Create a rectangle at position |
| `create-ellipse` | `x`, `y`, `width`, `height` | Create an ellipse at position |
| `create-frame` | `x`, `y`, `width`, `height` | Create a frame at position |
| `create-text` | `x`, `y`, `content` | Create a text layer with content |
| `create-line` | `x1`, `y1`, `x2`, `y2` | Create a line between two points |

### Properties
| Command | Params | Description |
|---------|--------|-------------|
| `set-position` | `x`, `y` | Set position of selected element |
| `set-size` | `width`, `height` | Set size of selected element |
| `set-corner-radius` | `radius` | Set corner radius of selected element |
| `set-rotation` | `degrees` | Set rotation angle of selected element |
| `set-opacity` | `percent` | Set opacity (0-100) of selected element |

### Fill & Stroke
| Command | Params | Description |
|---------|--------|-------------|
| `set-fill-color` | `hex` | Set fill color of selected element |
| `add-fill` | | Add a new fill to selected element |
| `remove-fill` | | Remove fill from selected element |
| `set-stroke-color` | `hex` | Set stroke color of selected element |
| `add-stroke` | | Add a stroke to selected element |
| `set-stroke-weight` | `weight` | Set stroke weight in pixels |

### Effects
| Command | Params | Description |
|---------|--------|-------------|
| `add-drop-shadow` | `x`, `y`, `blur`, `color` | Add drop shadow to selected element |
| `add-blur` | `amount` | Add blur effect to selected element |

### Typography
| Command | Params | Description |
|---------|--------|-------------|
| `set-font-family` | `family` | Set font family of selected text |
| `set-font-size` | `size` | Set font size of selected text |
| `set-font-weight` | `weight` | Set font weight (400, 700, etc.) |
| `set-line-height` | `value` | Set line height of selected text |
| `set-letter-spacing` | `value` | Set letter spacing of selected text |
| `text-align-left` | | Align text left |
| `text-align-center` | | Align text center |
| `text-align-right` | | Align text right |
| `text-align-justify` | | Justify text |
| `bold` | | Toggle bold on selected text |
| `italic` | | Toggle italic on selected text |
| `underline` | | Toggle underline on selected text |

### Auto Layout
| Command | Params | Description |
|---------|--------|-------------|
| `add-auto-layout` | | Add auto layout to selected frame |
| `remove-auto-layout` | | Remove auto layout from selected frame |
| `set-auto-layout-direction` | `direction` | Set direction: `horizontal` or `vertical` |
| `set-auto-layout-gap` | `gap` | Set spacing between children in pixels |
| `set-auto-layout-padding` | `top`, `right`, `bottom`, `left` | Set padding for auto layout frame |
| `set-auto-layout-resizing` | `axis`, `mode` | Set resizing: axis (`horizontal`/`vertical`), mode (`fixed`/`hug`/`fill`) |

### Layer Management
| Command | Params | Description |
|---------|--------|-------------|
| `group` | | Group selected layers |
| `ungroup` | | Ungroup selected group |
| `frame-selection` | | Wrap selected layers in a frame |
| `create-component` | | Create component from selected layers |
| `detach-instance` | | Detach component instance |
| `duplicate` | | Duplicate selected layers |
| `delete` | | Delete selected layers |
| `rename` | `name` | Rename selected layer |
| `bring-to-front` | | Bring selected layer to front |
| `send-to-back` | | Send selected layer to back |
| `bring-forward` | | Bring selected layer forward one step |
| `send-backward` | | Send selected layer backward one step |
| `lock` | | Toggle lock on selected layer |
| `hide` | | Toggle visibility of selected layer |

### Alignment
| Command | Description |
|---------|-------------|
| `align-left` | Align selected layers to left |
| `align-center-h` | Align selected layers to horizontal center |
| `align-right` | Align selected layers to right |
| `align-top` | Align selected layers to top |
| `align-center-v` | Align selected layers to vertical center |
| `align-bottom` | Align selected layers to bottom |
| `distribute-horizontal` | Distribute selected layers horizontally |
| `distribute-vertical` | Distribute selected layers vertically |

### Navigation
| Command | Description |
|---------|-------------|
| `zoom-to-fit` | Zoom to fit all content |
| `zoom-to-selection` | Zoom to fit selected layers |
| `zoom-100` | Reset zoom to 100% |
| `zoom-in` | Zoom in |
| `zoom-out` | Zoom out |
| `toggle-rulers` | Toggle rulers visibility |
| `toggle-grid` | Toggle grid visibility |

### Export
| Command | Params | Description |
|---------|--------|-------------|
| `export-selection` | | Export selected layers with current settings |
| `export-as-png` | `scale` | Export selected layers as PNG (scale: 1x, 2x, etc.) |
| `export-as-svg` | | Export selected layers as SVG |

### Boolean Operations
| Command | Description |
|---------|-------------|
| `union` | Union of selected shapes |
| `subtract` | Subtract top shape from bottom |
| `intersect` | Intersect selected shapes |
| `exclude` | Exclude overlapping areas |
| `flatten` | Flatten selected layers |
| `mask` | Create mask from selected layers |

### Design Templates
| Command | Params | Description |
|---------|--------|-------------|
| `create-button-component` | `label`, `width`, `height`, `fillColor`, `textColor`, `cornerRadius` | Create a reusable button component |
| `create-card-layout` | `width`, `height`, `padding`, `gap`, `cornerRadius` | Create a card with auto layout |
| `create-responsive-frame` | `width`, `height`, `direction`, `gap`, `padding` | Create a responsive auto layout frame |
| `create-icon-circle` | `size`, `fillColor` | Create a circular icon container |
| `create-input-field` | `width`, `height`, `placeholder`, `borderColor`, `cornerRadius` | Create a styled input field |

### State Queries
| Command | Returns | Description |
|---------|---------|-------------|
| `get-selection-size` | `width`, `height` | Get width and height of selected element |
| `get-selection-position` | `x`, `y` | Get position of selected element |
| `get-layer-name` | `name` | Get name of selected layer |

## Examples

```bash
# Build a login card
agent-browser --skill figma create-frame --x 400 --y 200 --width 360 --height 420
agent-browser --skill figma set-fill-color "#FFFFFF"
agent-browser --skill figma set-corner-radius 12
agent-browser --skill figma add-drop-shadow --x 0 --y 4 --blur 24 --color "#0000001A"
agent-browser --skill figma add-auto-layout
agent-browser --skill figma set-auto-layout-direction vertical
agent-browser --skill figma set-auto-layout-gap 16
agent-browser --skill figma set-auto-layout-padding --top 32 --right 32 --bottom 32 --left 32

# Add heading
agent-browser --skill figma create-text --x 0 --y 0 --content "Welcome Back"
agent-browser --skill figma set-font-size 24
agent-browser --skill figma set-font-weight 700

# Add email input
agent-browser --skill figma create-input-field --width 296 --height 44 --placeholder "Email" --borderColor "#D1D5DB" --cornerRadius 8

# Add password input
agent-browser --skill figma create-input-field --width 296 --height 44 --placeholder "Password" --borderColor "#D1D5DB" --cornerRadius 8

# Add sign-in button
agent-browser --skill figma create-button-component --label "Sign In" --width 296 --height 44 --fillColor "#3B82F6" --textColor "#FFFFFF" --cornerRadius 8
```

```bash
# Build a button system with variants
agent-browser --skill figma create-button-component --label "Primary" --width 120 --height 40 --fillColor "#3B82F6" --textColor "#FFFFFF" --cornerRadius 8
agent-browser --skill figma duplicate
agent-browser --skill figma set-fill-color "#10B981"
agent-browser --skill figma rename "Button / Success"

agent-browser --skill figma duplicate
agent-browser --skill figma set-fill-color "#EF4444"
agent-browser --skill figma rename "Button / Danger"

agent-browser --skill figma duplicate
agent-browser --skill figma set-fill-color "#F59E0B"
agent-browser --skill figma rename "Button / Warning"
```

```bash
# Set up a responsive frame with header and content
agent-browser --skill figma create-responsive-frame --width 1440 --height 900 --direction vertical --gap 0 --padding 0

# Header bar
agent-browser --skill figma create-frame --x 0 --y 0 --width 1440 --height 64
agent-browser --skill figma set-fill-color "#1E293B"
agent-browser --skill figma add-auto-layout
agent-browser --skill figma set-auto-layout-direction horizontal
agent-browser --skill figma set-auto-layout-padding --top 12 --right 24 --bottom 12 --left 24

# Logo text
agent-browser --skill figma create-text --x 0 --y 0 --content "MyApp"
agent-browser --skill figma set-font-size 20
agent-browser --skill figma set-font-weight 700
agent-browser --skill figma set-fill-color "#FFFFFF"

# Content area
agent-browser --skill figma create-responsive-frame --width 1440 --height 836 --direction horizontal --gap 24 --padding 24
agent-browser --skill figma set-fill-color "#F8FAFC"
```

## Troubleshooting

**Can't connect to Figma?**
- Make sure Figma Desktop is running with `--remote-debugging-port=9226`
- Check if port 9226 is available: `lsof -i :9226`
- Figma must be the Desktop app, not the browser version

**Selectors not working?**
- Figma updates may change the UI structure
- Run `agent-browser snapshot` to see current element refs
- Submit an issue or PR to update selectors

**Keyboard shortcuts not firing?**
- Make sure the Figma canvas has focus before running tool commands
- Run `agent-browser --skill figma tool-move` first to ensure the canvas is active
- Some shortcuts only work when specific layer types are selected
