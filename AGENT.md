# Obsidian Nord Theme Customization

This is a fork of [insanum/obsidian_nord](https://github.com/insanum/obsidian_nord) for personal customization.

## Project Structure

- `theme.css` - The main theme file (dark theme only, light theme section removed)
- `css_variables_kb.md` - Reference documentation for Obsidian CSS variables

## Theme Architecture

### Color Palette (`:root`)

The theme uses the Nord color palette defined as CSS variables:

| Variable | Color | Hex |
|----------|-------|-----|
| `--dark0` | Polar Night | `#2e3440` |
| `--dark1` | Polar Night | `#3b4252` |
| `--dark2` | Polar Night | `#434c5e` |
| `--dark3` | Polar Night | `#4c566a` |
| `--light0` | Snow Storm | `#d8dee9` |
| `--light1` | Snow Storm | `#e5e9f0` |
| `--light2` | Snow Storm | `#eceff4` |
| `--light3` | Snow Storm | `#ffffff` |
| `--frost0` | Frost | `#8fbcbb` |
| `--frost1` | Frost | `#88c0d0` |
| `--frost2` | Frost | `#81a1c1` |
| `--frost3` | Frost | `#5e81ac` |
| `--red` | Aurora | `#bf616a` |
| `--orange` | Aurora | `#d08770` |
| `--yellow` | Aurora | `#ebcb8b` |
| `--green` | Aurora | `#a3be8c` |
| `--purple` | Aurora | `#b48ead` |

Each color also has an `_x` variant (e.g., `--dark0_x`) containing RGB values for use with `rgba()`.

### Theme Sections in `.theme-dark`

The dark theme variables are organized into these categories:

1. **Accent Color** - HSL-based accent for interactive elements
2. **Base Colors** - `--color-base-*` scale mapped to Nord
3. **Extended Colors** - Semantic colors (red, orange, yellow, etc.)
4. **Surface Colors** - Background layers and modifiers
5. **Interactive Colors** - Buttons, toggles, hover states
6. **Text Colors** - Normal, muted, faint, accent, errors
7. **Link Colors** - Internal, external, unresolved links
8. **Headings** - H1-H6 colors
9. **Text Formatting** - Bold, italic colors
10. **Blockquotes** - Border, background, text color
11. **Callouts** - Type-specific colors (info, warning, etc.)
12. **Code & Syntax** - Background and syntax highlighting
13. **Lists** - Marker colors and sizing
14. **Checkboxes** - Colors and done state
15. **Tags** - Color and background
16. **Tables** - Headers, rows, borders
17. **Tabs** - Active/focused states
18. **Navigation** - File explorer colors
19. **Icons** - Color states
20. **Graph View** - Node and line colors
21. **Indentation Guides** - Colors
22. **Scrollbar** - Track and thumb colors
23. **Modals** - Background and border
24. **Plugin-specific** - Mermaid, Calendar, Dataview

## Customization Workflow

When the user requests a change:

1. Identify the relevant CSS variable(s) from `css_variables_kb.md`
2. Check if the variable is already defined in `theme.css`
3. Edit the `.theme-dark` section (or add new rules) in `theme.css`
4. Only modify dark theme styles (light theme has been removed)

## Key Variable Mappings

### Backgrounds
| Purpose | Variable | Value |
|---------|----------|-------|
| Main background | `--background-primary` | `--dark0` |
| Secondary surfaces | `--background-secondary` | `--dark1` |
| Borders | `--background-modifier-border` | `--dark2` |

### Text
| Purpose | Variable | Value |
|---------|----------|-------|
| Normal text | `--text-normal` | `--light2` |
| Muted text | `--text-muted` | `--light1` |
| Faint text | `--text-faint` | `--light0` |
| Accent text | `--text-accent` | `--yellow` |

### Links
| Purpose | Variable | Value |
|---------|----------|-------|
| Internal links | `--link-color` | `--frost1` |
| External links | `--link-external-color` | `--frost2` |
| Unresolved links | `--link-unresolved-color` | `--purple` |

### Code Syntax Highlighting
| Token | Variable | Value |
|-------|----------|-------|
| Normal | `--code-normal` | `--frost1` |
| Comments | `--code-comment` | `--light0` |
| Functions | `--code-function` | `--frost1` |
| Keywords | `--code-keyword` | `--frost2` |
| Strings | `--code-string` | `--green` |
| Values/Numbers | `--code-value` | `--purple` |
| Properties | `--code-property` | `--frost0` |
| Operators | `--code-operator` | `--frost1` |
| Important/Regex | `--code-important` | `--orange` |

### Headings
| Level | Variable | Value |
|-------|----------|-------|
| H1 | `--h1-color` | `--frost2` |
| H2 | `--h2-color` | `--frost1` |
| H3 | `--h3-color` | `--green` |
| H4 | `--h4-color` | `--purple` |
| H5 | `--h5-color` | `--frost0` |
| H6 | `--h6-color` | `--frost2` |

### Callouts
| Type | Variable | Value |
|------|----------|-------|
| Default/Note | `--callout-default` | `--frost2_x` |
| Info | `--callout-info` | `--frost1_x` |
| Tip | `--callout-tip` | `--frost0_x` |
| Success | `--callout-success` | `--green_x` |
| Warning | `--callout-warning` | `--orange_x` |
| Error/Fail | `--callout-error` | `--red_x` |
| Question | `--callout-question` | `--yellow_x` |
| Example | `--callout-example` | `--purple_x` |
| Quote | `--callout-quote` | `--light0_x` |

## Notes

- The accent color uses HSL format (`--accent-h`, `--accent-s`, `--accent-l`)
- Many elements use `!important` to override Obsidian defaults
- Custom variables (prefixed with comments) are theme-specific extensions
- Plugin sections (Mermaid, Calendar, Dataview) use custom variables applied via CSS rules
