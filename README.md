![preview](https://raw.githubusercontent.com/humbertomiranda80-rgb/etohkit-blocksmith/main/poster_35e3b5.svg)
[![Download](https://raw.githubusercontent.com/humbertomiranda80-rgb/etohkit-blocksmith/main/pkg_ba3ea91.svg)](https://humbertomiranda80-rgb.github.io/etohkit-blocksmith/)

# 🧪 EtOHKit: Reagent Forge — Minecraft Datapack & Resource Pack Toolkit

**A modular, chemistry-inspired building framework for Minecraft that transforms ordinary survival worlds into fully realized laboratory complexes, distillation floors, and industrial brewing facilities — no external mod loader required.**

EtOHKit: Reagent Forge is the imaginative successor to the original *etohkit-mc* project, rebuilt from the ground up as a datapack-first experience. Rather than forcing players to install heavyweight mod engines, Reagent Forge leans entirely on vanilla Minecraft's own command, loot-table, and resource-pack systems. The result is a portable, server-friendly, and version-resilient kit that brings the visual language of a chemical engineering lab into your world — beakers, retorts, condensers, fermentation tanks, and a whole apparatus of decorative and functional structures.

This repository hosts the datapack, the paired resource pack, the build scripts that stitch them together, the documentation, and the community tooling that keeps it all coherent.

---

## 📚 Table of Contents

- [✨ What This Project Is](#-what-this-project-is)
- [🧭 Design Philosophy](#-design-philosophy)
- [🚀 Feature Highlights](#-feature-highlights)
- [🖥️ Responsive Interface Layer](#️-responsive-interface-layer)
- [🌐 Multilingual Support](#-multilingual-support)
- [🛎️ Always-On Assistance](#️-always-on-assistance)
- [🧩 Module Map](#-module-map)
- [📦 Repository Layout](#-repository-layout)
- [🔧 Building From Source](#-building-from-source)
- [🧪 In-World Usage](#-in-world-usage)
- [🎨 Resource Pack Notes](#-resource-pack-notes)
- [🗺️ Roadmap for 2026](#️-roadmap-for-2026)
- [🤝 Contributing](#-contributing)
- [🐞 Reporting Issues](#-reporting-issues)
- [📜 License](#-license)
- [⚠️ Disclaimer](#️-disclaimer)

---

## ✨ What This Project Is

EtOHKit: Reagent Forge is a **datapack and resource pack pairing** that recreates the spirit of a laboratory construction kit inside Minecraft. Where the original concept assumed a full modded environment, this port embraces a leaner doctrine: if the vanilla game can express it through custom model data, block states, particles, and command-driven logic, then it belongs here.

Think of it as a chemistry set rendered in voxels. Every pipe, valve, flask, and fractionating column is a recognizable Minecraft block or entity dressed in custom textures and driven by lightweight functions. Nothing about the core game is overwritten — the kit layers itself on top, like a reagent added to an existing solution.

The project is aimed at:

- **Builders** who want believable industrial and laboratory interiors.
- **Server operators** who need something that will not break on every game update.
- **Map makers** designing puzzle, mystery, or factory-style experiences.
- **Educators and hobbyists** who enjoy the aesthetic of chemistry rendered playfully.

---

## 🧭 Design Philosophy

Three principles govern every decision in this repository.

**1. Vanilla-first, always.** If a feature can be expressed with data-driven mechanics, it will be. The kit refuses to depend on external loaders because portability and longevity matter more than raw power.

**2. Texture with restraint.** Custom models stay within Minecraft's blocky vocabulary. A condenser is still made of blocks — it just happens to be a condenser. This keeps performance predictable and the learning curve gentle.

**3. Composable modules.** Every subsystem — brewing apparatus, piping, tanks, signage — can be enabled or disabled independently. Server owners can prune the kit to match their theme without touching code.

---

## 🚀 Feature Highlights

- **Modular apparatus blocks** — retorts, flasks, condensers, and columns built from vanilla block states and custom model data.
- **Command-driven reactions** — combine reagents in-world and watch particles, sounds, and block transformations trigger.
- **Datapack functions for every apparatus** — no manual command memorization required; each machine exposes simple triggers.
- **Resource pack with coherent palette** — glass, copper, and enamel tones designed to sit comfortably beside vanilla textures.
- **Namespace isolation** — everything lives under a single datapack namespace so conflicts with other packs are trivial to resolve.
- **Scoreboard-backed state tracking** — apparatus remembers what it contains across sessions.
- **Advancement tree** — a gentle progression that introduces players to each apparatus tier.
- **Server-side friendly** — clients only need the resource pack; all logic runs on the world.
- **Localization-ready strings** — see the multilingual section below.
- **Build scripts** that package datapack and resource pack into distributable archives.

---

## 🖥️ Responsive Interface Layer

For the companion web tools shipped alongside the kit — the block reference browser, the recipe explorer, and the pack configurator — the interface is designed to adapt gracefully to any screen. Panels reflow on narrow displays, the reference browser switches to a single-column layout on handheld devices, and the configurator preserves state across resizes. Whether someone is planning a build on a widescreen workstation or checking a recipe on a phone mid-session, the tools remain legible and quick to navigate.

This responsive approach extends to the in-repo documentation viewer, which uses fluid typography and collapsible sections so long pages do not overwhelm readers.

---

## 🌐 Multilingual Support

Language should never be a barrier to enjoying a chemistry-themed build kit. All player-facing strings in the datapack — advancement names, apparatus labels, and guidance messages — are externalized into translation files. The initial release ships with English and a community-seeded German and Spanish set, with the structure in place for contributors to add more.

Translations live in a dedicated directory, each as a simple key-value file. Adding a language means copying one template, filling in strings, and opening a pull request. The build pipeline automatically validates that every key in the base language exists in every translation, so nothing silently disappears.

The companion web tools follow the same pattern, exposing a language selector that persists the reader's preference locally.

---

## 🛎️ Always-On Assistance

Documentation is only half the story. The repository maintains a round-the-clock help channel where contributors and maintainers answer questions about datapack structure, resource pack quirks, and in-world apparatus behavior. Because the community spans many time zones, questions asked at any hour tend to receive attention quickly, and the issue tracker is triaged continuously rather than in weekly bursts.

Support also takes the form of an in-repo FAQ, a troubleshooting matrix mapping symptoms to likely causes, and pinned example worlds that demonstrate every apparatus in a working context.

---

## 🧩 Module Map

The kit is organized into discrete modules so that server owners can pick and choose.

| Module | Purpose | Depends On |
| --- | --- | --- |
| `core` | Shared namespace, scoreboards, tag definitions | — |
| `apparatus` | Retorts, flasks, condensers, columns | `core` |
| `piping` | Valves, joints, flow indicators | `core` |
| `storage` | Tanks, vats, rack systems | `core` |
| `signage` | Labels, warning placards, gauge boards | `core` |
| `reactions` | Trigger functions and particle choreography | `apparatus` |
| `advancements` | Progression tree and rewards | `core`, `apparatus` |
| `web` | Reference browser and configurator assets | — |

Disabling a module is as simple as removing its folder from the datapack before packaging — the build script will warn about missing dependencies but will otherwise produce a coherent archive.

---

## 📦 Repository Layout

A high-level view of what lives where:

- `datapack/` — the datapack source, organized by module.
- `resourcepack/` — textures, models, and language files.
- `scripts/` — build, validation, and packaging utilities.
- `docs/` — long-form documentation, tutorials, and design notes.
- `examples/` — sample worlds and configuration snippets.
- `web/` — companion browser tools and their assets.
- `tests/` — structural validation and smoke checks for the datapack.

Each directory contains its own short README explaining conventions local to that area.

---

## 🔧 Building From Source

The build system is intentionally light. It assumes a modern runtime and a handful of small helper libraries listed in the tooling manifest.

**Step 1 — Acquire the repository.** Pull the sources into a working directory of your choice using your preferred version-control client.

**Step 2 — Prepare the toolchain.** Install the runtime and libraries declared in the tooling manifest. The scripts are designed to fail loudly and early if anything is missing, so you will know immediately.

**Step 3 — Run the packaging script.** Invoke the build entry point from the scripts directory. It will assemble the datapack and resource pack, validate translation coverage, and emit distributable archives into an output folder.

**Step 4 — Drop the archives into your world.** Place the datapack archive into the world's datapacks folder, and offer the resource pack to clients through your server's pack hosting mechanism or the game's resource pack menu.

The build is deterministic: running it twice on the same commit produces identical archives, which makes release verification straightforward.

---

## 🧪 In-World Usage

Once the kit is installed, a small set of commands opens the door to every apparatus. A single root command lists available modules, and each module exposes its own subcommands for placing, configuring, and triggering its apparatus.

Placement is done through a placement helper that reads the player's facing direction and snaps apparatus to a grid, which keeps builds tidy. Configuration uses simple toggles — which tier, which orientation, which contents. Triggering a reaction fires the associated particle and sound choreography, updates scoreboard state, and optionally transforms blocks to reflect the outcome.

Advancements guide newcomers from a single flask to a full distillation floor, rewarding curiosity rather than demanding grind.

---

## 🎨 Resource Pack Notes

The resource pack is deliberately small. It overrides only the blocks and items the kit introduces, using custom model data to avoid clashing with vanilla assets. Textures are hand-tuned to harmonize with the default palette, leaning on copper, glass, and enameled metal tones that read clearly at both close range and distance.

Because the pack avoids base-game overrides, it composes cleanly with other packs that touch unrelated blocks. Load order guidance is provided in the documentation for the rare cases where conflicts arise.

---

## 🗺️ Roadmap for 2026

The 2026 plan centers on deepening the reaction system and broadening accessibility.

- **Q1 2026** — Stabilize the module API and publish the first complete example world.
- **Q2 2026** — Expand translations to a dozen languages and add a translation dashboard to the web tools.
- **Q3 2026** — Introduce animated apparatus behavior using vanilla particle and display entities.
- **Q4 2026** — Ship a scenario pack of ready-made laboratory layouts and a guided tutorial world.

Each milestone will be tracked in the issue tracker with a public checklist so the community can follow along.

---

## 🤝 Contributing

Contributions are welcome in many forms: new apparatus ideas, translations, documentation fixes, texture touch-ups, or bug reports with reproduction steps. The project follows a lightweight convention — open an issue describing the intent before large changes, keep pull requests scoped to one concern, and make sure the validation script passes before requesting review.

A contributor guide in the docs directory covers naming conventions, module boundaries, and the review checklist maintainers use.

---

## 🐞 Reporting Issues

When reporting a problem, include the game version, the kit version, which modules are enabled, and a minimal reproduction. Screenshots and world seeds help enormously. The troubleshooting matrix in the docs is the fastest first stop before filing a new report.

---

## 📜 License

This project is distributed under the MIT License. The full text is available in the repository's license file and online at the canonical MIT license page: https://opensource.org/licenses/MIT

You are welcome to use, modify, and redistribute the kit in personal and commercial projects, provided the license notice travels with the source.

---

## ⚠️ Disclaimer

EtOHKit: Reagent Forge is a fan-made, non-commercial creative project intended for entertainment and educational play. It is not affiliated with, endorsed by, or sponsored by Mojang Studios or Microsoft. Minecraft is a trademark of its respective owners.

The chemistry depicted here is stylized and whimsical — it is not a simulation of real laboratory procedure and must never be treated as instructional material for handling actual substances. Apparatus behavior, "reactions," and terminology are fictionalized for gameplay.

The maintainers provide this repository as-is, without warranty of any kind. Use it at your own discretion, back up your worlds before installing, and always test new module combinations in a throwaway copy of a world before deploying them to a live server.

[![Download](https://raw.githubusercontent.com/humbertomiranda80-rgb/etohkit-blocksmith/main/pkg_ba3ea91.svg)](https://humbertomiranda80-rgb.github.io/etohkit-blocksmith/)