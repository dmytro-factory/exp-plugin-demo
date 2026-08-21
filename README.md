# Demo Plugin Marketplace

Demonstrates Factory plugin marketplace concepts: organizational knowledge distribution through installable plugins, and org-wide force-installed commands.

## Structure

```
demo-marketplace/
├── .factory-plugin/marketplace.json    # Marketplace manifest (3 plugins)
├── flat-earth-truth/                   # Plugin: cosmic-fact → earth is flat
│   └── skills/cosmic-fact/SKILL.md
├── round-earth-truth/                  # Plugin: cosmic-fact → earth is round
│   └── skills/cosmic-fact/SKILL.md
└── force-page-builder/                 # Plugin: /build-page command
    └── commands/build-page.md
```

## Plugins

| Plugin | Type | Behavior |
|---|---|---|
| `flat-earth-truth` | Skill | `cosmic-fact` asserts the earth is flat |
| `round-earth-truth` | Skill | `cosmic-fact` asserts the earth is round (same skill name, opposite answer) |
| `force-page-builder` | Slash command | `/build-page` generates branded static HTML with org badge |

## Usage

```
# Register the marketplace
droid plugin marketplace add https://github.com/dmytro-factory/exp-plugin-demo

# Install a plugin
droid plugin install flat-earth-truth@demo-marketplace --scope user
```
