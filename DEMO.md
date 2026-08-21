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

> **Narrative:** "Our marketplace has two project plugins. Both provide the same skill — `project-context` — but each encodes a different project's conventions. Let me show you."

**Step 1 — Install the Atlas plugin:**

```
droid plugin install atlas-project@demo-marketplace --scope user
```

**Step 2 — Ask Droid:**

> "How should I structure a new feature?"

Droid activates the `project-context` skill. Answer: feature-based directory under `src/features/`, functional components with hooks, strict TypeScript, Tailwind utilities, Zustand for state, TanStack Query for server state.

**Step 3 — Switch plugins:**

```
droid plugin uninstall atlas-project@demo-marketplace --scope user
droid plugin install orion-project@demo-marketplace --scope user
```

**Step 4 — Same question:**

> "How should I structure a new feature?"

Same skill name (`project-context`). Completely different answer: layered architecture with routers → services → repositories, async endpoints, Pydantic models for validation, dependency injection via FastAPI's `Depends`, pytest-asyncio for tests.

> **Key point:** "The model didn't change. The prompt didn't change. Only the plugin changed. This is organizational knowledge distribution — different teams install plugins that encode their project conventions, and Droid adapts instantly."

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
droid plugin uninstall atlas-project@demo-marketplace --scope user    # if still installed
droid plugin uninstall orion-project@demo-marketplace --scope user    # if still installed
droid plugin marketplace remove demo-marketplace
```
