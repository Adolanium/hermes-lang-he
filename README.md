<div align="center" dir="auto">

  # Hermes in Hebrew · עברית

  **A Hebrew language pack for Hermes Agent: the CLI, the messaging gateway, the TUI and Hermes Desktop.**

  Right-to-left layout in Desktop, Hebrew prompts in the terminal, Hebrew replies from the gateway's built-in messages.

  <sub>POWERED BY <a href="https://github.com/NousResearch/hermes-agent">HERMES AGENT</a> &nbsp;·&nbsp; COMMUNITY PLUGIN &nbsp;·&nbsp; VERSION 0.1.0</sub>

</div>

## What it covers

Hermes does not ship Hebrew, so this pack brings all three catalogs:

| Surface | File | Covers |
| --- | --- | --- |
| Core | `locales/he.yaml` | CLI prompts and messages, approval prompts, gateway replies, platform messages, tips |
| TUI | `locales/he.tui.yaml` | `hermes --tui`: status bar, composer, hotkey help, prompts |
| Desktop | `locales/he.desktop.yaml` | Hermes Desktop, with the layout flipped to right-to-left |

Each file's header says how many keys it translates and which Hermes commit it was checked against. Anything the pack does not translate falls back to English, so a newer Hermes never shows a blank label.

What stays in English:

- What the agent itself writes. Ask it to answer in Hebrew in your prompt or in `SOUL.md`.
- Commands, flags, config keys, environment variables, file paths and product names, so they still match what you type.
- A handful of Desktop and TUI labels whose English wording changes with an argument (Show/Hide, on/off). The pack format can only carry one wording for those, so they keep the correct English text instead of a Hebrew one that would be wrong half the time.

## Install

```sh
hermes plugins install Adolanium/hermes-lang-he
hermes config set display.language he
```

Restart a running gateway or TUI so it picks up the pack. In Desktop, pick **עברית** in the language switcher.

The pack needs Hermes Agent 0.21.6 or later.

## What it does on your machine

Nothing beyond adding text. The pack is three YAML catalogs and a manifest. It makes no network calls, reads nothing outside its own folder and runs no code. `__init__.py` exists only so Desktop's "Install from Git" accepts the pack ([hermes-agent#138118](https://github.com/NousResearch/hermes-agent/issues/138118)); its `register()` does nothing. Installing the pack never changes your language: you opt in with `display.language`.

## Keeping it current

Hermes adds and renames strings often. To see what changed against a hermes-agent checkout:

```sh
python tools/sync_keys.py ../hermes-agent
python tools/sync_keys.py ../hermes-agent --missing missing.txt   # list untranslated keys
python tools/sync_keys.py ../hermes-agent --fix                   # drop keys Hermes no longer has
```

Then check the pack with Hermes's own validator:

```sh
hermes plugins validate .
```

## Translation notes

- Gender-neutral wording throughout: impersonal forms ("יש ל…", "אפשר ל…") and verbal nouns for buttons ("שמירה", "סגירה").
- Terms: session = סשן, skill = מיומנות, plugin = תוסף, profile = פרופיל, provider = ספק, agent = סוכן.
- The Desktop catalog started from the Hebrew translation proposed in [hermes-agent#124840](https://github.com/NousResearch/hermes-agent/pull/124840), brought up to date with current Hermes.

Corrections are welcome as issues or pull requests.

## License

MIT
