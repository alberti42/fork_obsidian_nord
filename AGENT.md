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

---

## Design Decisions & Analysis

This section documents issues we identified during theme analysis and the decisions made. These are not hard rules - future changes may revisit these decisions.

### 1. Custom Theme-Specific Variables

**Analysis:** The theme defines several variables that are not part of Obsidian's official CSS API. These are internal helpers used within the theme's CSS rules.

| Variable | Purpose | Used By |
|----------|---------|---------|
| `--cursor-line-background` | Active line highlight in editor | `.cm-active` rule |
| `--flashing-background` | Search result flash animation | `.is-flashing` rule |
| `--text-highlight-fg` | Foreground color for highlighted text | `.markdown-rendered mark`, `.cm-highlight` |
| `--mermaid-note`, `--mermaid-loopline`, etc. | Mermaid diagram styling | `.mermaid` rules |
| `--calendar-*` | Calendar plugin styling | `.calendar` rules |
| `--dataview-*` | Dataview plugin styling | `.dataview` rules |
| `--nav-file-tag` | File count badges in navigator | `.nav-file-tag` rule |
| `--table-row-even-background`, `--table-row-odd-background` | Alternating table rows | `tbody tr:nth-child` rules |
| `--nord-table-*` | Intermediate Nord colors for tables | Table variables |

**Decision:** Keep these variables. They work correctly because they're applied via explicit CSS rules. They provide meaningful names and make the theme easier to customize. The `--text-highlight-fg` is particularly useful as Obsidian only provides `--text-highlight-bg` officially.

### 2. Use of `!important` Declarations

**Analysis:** The theme uses `!important` on many CSS rules to override Obsidian's default styles. Examples:
- Table styling (`background-color: var(--table-row-even-background) !important`)
- Mark/highlight styling
- Search result text color
- Bold text in editor

**Decision:** Keep all `!important` declarations. Removing them is risky - Obsidian's default styles may have higher specificity, causing the theme to break. The current approach is safer and works reliably.

### 3. Hardcoded Values (Resolved)

**Analysis:** The original theme had hardcoded HSL values for table colors:
- `hsl(220, 16%, 16%)` for table headers
- `hsl(220, 16%, 20%)` for even rows
- `hsl(220, 16%, 24%)` for odd rows

These used Nord's blue-tinted gray hue but weren't part of the variable system.

**Decision:** Replaced with Nord-based variables (`--nord-table-header`, `--nord-table-row-even`, `--nord-table-row-odd`) defined in `:root`. This maintains visual consistency while integrating with the variable system. Each has an `_x` RGB variant for potential `rgba()` usage.

### 4. Non-Standard Variable Names (Resolved)

**Analysis:** Some variables didn't match Obsidian's official API:
- `--inline-title-fg-color` (should be `--inline-title-color`)
- `--link-url` (not an official variable)

**Decision:** Fixed these to use official names where they exist. The `.cm-url` rule now uses `--yellow` directly instead of a non-existent variable.

### 5. Missing Official Variables (Resolved)

**Analysis:** The original theme was missing many official Obsidian CSS variables, which could cause inconsistent behavior or fall back to Obsidian defaults.

**Decision:** Added comprehensive coverage of official variables:
- Base colors (`--color-base-00` to `--color-base-100`)
- Code syntax highlighting (11 token types)
- Blockquote styling
- Callout type colors (14 types)
- Link colors (internal, external, unresolved)
- List markers
- Interactive elements
- Surface modifiers
- And more (see Theme Sections above)

### 6. Plugin-Specific Styling

**Analysis:** The theme includes styling for third-party plugins (Mermaid, Calendar, Dataview). These use custom variables that only work because they're applied via CSS rules targeting plugin-specific classes.

**Decision:** Keep these sections. They're isolated and don't affect core functionality. If a plugin isn't installed, the rules simply don't apply. This provides a better experience for users of these popular plugins.
