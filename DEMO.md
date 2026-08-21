# Demo Script: Plugin Marketplaces & Organizational Knowledge Distribution

Repo: https://github.com/dmytro-factory/exp-plugin-demo
Marketplace name: `demo-marketplace`

---

## Before the demo (one-time setup)

### 1. Register the marketplace

On both your machine and the demo machine (Droid computer):

```
droid plugin marketplace add https://github.com/dmytro-factory/exp-plugin-demo
```

Verify it shows 3 plugins:

```
droid plugin marketplace list
```

### 2. Force-install page-builder (org-managed settings)

In Factory app → Enterprise Controls → Org Settings, add:

```json
{
  "extraKnownMarketplaces": {
    "demo-marketplace": {
      "source": {
        "source": "github",
        "repo": "dmytro-factory/exp-plugin-demo"
      }
    }
  },
  "enabledPlugins": {
    "force-page-builder@demo-marketplace": true
  }
}
```

This ensures every user in your org automatically has the `/build-page` command.

### 3. Verify on the demo machine

On the Droid computer, log in as the demo user and confirm:

```
droid plugin list --scope org
```

You should see `force-page-builder@demo-marketplace` already installed. Try `/build-page Hello World` to confirm it works.

---

## During the demo

### Act 1: Same question, different answer (skill switching)

> **Narrative:** "Our marketplace has two competing plugins. Both provide the same skill — `cosmic-fact` — but with completely different organizational knowledge baked in. Let me show you."

**Step 1 — Install the flat-earth plugin:**

```
droid plugin install flat-earth-truth@demo-marketplace --scope user
```

**Step 2 — Ask Droid:**

> "What shape is the earth?"

Droid activates the `cosmic-fact` skill. Answer: the earth is flat. Disc model, ice wall, NASA conspiracy, gravity doesn't exist.

**Step 3 — Switch plugins:**

```
droid plugin uninstall flat-earth-truth@demo-marketplace --scope user
droid plugin install round-earth-truth@demo-marketplace --scope user
```

**Step 4 — Same question:**

> "What shape is the earth?"

Same skill name (`cosmic-fact`). Completely opposite answer: oblate spheroid, satellite evidence, centuries of observation.

> **Key point:** "The model didn't change. The prompt didn't change. Only the plugin changed. This is organizational knowledge distribution — different teams can install different plugins that encode their domain truth, and Droid adapts instantly."

### Act 2: Force-installed command (org-wide governance)

> **Narrative:** "Some plugins aren't optional. The platform team can force-install capabilities that every engineer needs. Watch."

**Step 5 — Use the force-installed command:**

```
/build-page Create a welcome page for new engineering hires with onboarding steps
```

Droid generates a complete static HTML page with dark branding, org badge in the header, and a red "FORCE INSTALLED" badge in the footer.

> **Key point:** "This command was never manually installed by this user. It arrived automatically through org-managed settings. Every engineer in the org has it — consistent tooling, zero setup."

### Act 3 (optional): Browse the marketplace

Open `/plugins` in Droid → Browse tab → show `demo-marketplace` with its 3 plugins, descriptions, categories.

---

## Cleanup after the demo

```
droid plugin uninstall flat-earth-truth@demo-marketplace --scope user   # if still installed
droid plugin uninstall round-earth-truth@demo-marketplace --scope user  # if still installed
droid plugin marketplace remove demo-marketplace
```
