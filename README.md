# Demo Plugin Marketplace

Demonstrates Factory plugin marketplace concepts: organizational knowledge distribution through installable plugins, and org-wide force-installed commands.

## Structure

```
.factory-plugin/marketplace.json        # Marketplace manifest (3 plugins)
atlas-project/                         # Plugin: project-context → Atlas (React/TS)
└── skills/project-context/SKILL.md
orion-project/                         # Plugin: project-context → Orion (Python/FastAPI)
└── skills/project-context/SKILL.md
force-page-builder/                    # Plugin: /build-page command
└── commands/build-page.md
```

## Plugins

| Plugin | Type | Behavior |
|---|---|---|
| `atlas-project` | Skill | `project-context` encodes Atlas conventions (React 18, TypeScript, Tailwind, Zustand) |
| `orion-project` | Skill | `project-context` encodes Orion conventions (Python, FastAPI, SQLAlchemy, async) |
| `force-page-builder` | Slash command | `/build-page` generates branded static HTML with org badge |

Both project plugins provide the same skill (`project-context`) but with different conventions. Switching plugins changes Droid's project knowledge instantly.

## Usage

```
# Register the marketplace
droid plugin marketplace add https://github.com/dmytro-factory/exp-plugin-demo

# Install a plugin
droid plugin install atlas-project@demo-marketplace --scope user
```
