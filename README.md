# NativeClaw

NativeClaw is a **local-first Android agent app** built around an **on-device LiteRT LLM runtime**, a **chat-first UI**, **background execution**, **custom system prompts**, **importable skills**, and **runtime observability**.

It is designed for people who want an Android agent that stays **private by default**, runs **mostly on-device**, can be **customized deeply**, and exposes enough visibility to understand what the agent did and why.

> This public repository is intentionally **README-only** for now.  
> The full source code currently lives in a **private repository** while the project is still being hardened, validated on real devices, and prepared for a cleaner public release.

---

## Why NativeClaw

NativeClaw focuses on a few core strengths:

- **Local-first**: model execution is designed around local LiteRT-compatible models
- **Private by default**: prompts, history, traces, settings, and skills are stored on-device
- **Background-capable**: a foreground service keeps the agent available beyond the visible UI
- **Customizable**: behavior is shaped by prompt layers, additional instructions, skills, and tool contracts
- **Traceable**: history, logs, token estimates, and runtime traces are persisted for inspection
- **Extensible**: supports built-in skills, imported markdown skills, and JS-backed skill packages

---

## Current capabilities

### Core agent runtime
- On-device LiteRT runtime integration
- Foreground background-agent service
- Chat messages routed into the same runtime queue used by other triggers
- Configurable runtime settings for:
  - model path
  - context window
  - top-k
  - top-p
  - temperature
  - seed
  - thinking mode
  - backend preference

### Chat-first app UX
Main app areas currently include:
- **Chat**
- **Runtime**
- **Settings**
- **Permissions**
- **History**
- **Logs**
- **Help**

Other UX capabilities include:
- persistent chat sessions
- prompt library with add/delete/load support
- image attachments in the composer
- audio recording attachments in the composer
- multimodal request flow with text-summary fallback when direct media handling is unavailable
- a dedicated permissions screen to review and grant required Android access

### Prompt harness
- fixed system prompt files seeded from assets
- effective prompt assembly from:
  - base prompt
  - behavior rules
  - user additional instructions
  - enabled skill summaries
  - direct tool guidance
  - runtime context
- prompt preview in the UI

### Skills and extensibility
- Room-backed skill registry
- support for:
  - standalone `SKILL.md` skills
  - JS-backed skill packages
- built-in and user-managed skills
- enable/disable/edit/delete skill flows in Settings
- import foundations for markdown and package-based skills
- `readSkill(name)` model-discoverable skill loading approach
- JS skill execution via WebView bridge

### Background triggers
- direct UI chat input
- scheduled tasks via WorkManager
- notification listener ingestion
- push/FCM event ingestion foundation
- unified queue for all agent triggers

### Native tool foundation
NativeClaw already includes coded tool families behind skill discovery, including support for flows such as:

- Android app handoff and intents
- opening URLs, search, maps, dialer, SMS, email, and share sheet
- settings handoff
- calendar access and event creation
- contacts creation and search
- alarms and timers
- notification reading, clearing, and posting
- app-local file read/write
- Android-visible file search
- lightweight memory and variable storage

### Observability and traceability
- persisted runtime logs
- session history
- raw inference traces
- transcript events
- estimated token counts
- heap and CPU sampling before/after inference
- error visibility for runtime and inference failures

### Model management
- manual local model path support
- built-in background model downloads
- download progress and cancellation
- current built-in model entries include:
  - `Gemma-4-E2B-it`
  - `Gemma-4-E4B-it`

---

## Architecture at a glance

Main building blocks:

- **Compose UI** for chat, runtime, settings, permissions, history, and logs
- **Foreground service** for active agent runtime work
- **WorkManager** for scheduled triggers and background downloads
- **LiteRT runtime layer** for local inference
- **Room** for chat, logs, skills, schedules, observability, and prompt data
- **DataStore** for settings
- **Prompt harness** for effective system prompt composition
- **Skill library** for markdown and JS-backed capabilities
- **Unified event queue** so chat, schedules, notifications, and push flow through the same processing path

---

## Android permissions and access model

NativeClaw currently declares or uses access related to:

User-controlled access:
- **Camera** — for photo attachments
- **Microphone / record audio** — for audio attachments
- **Contacts** — for contact lookup tools
- **Calendar** — for calendar lookup tools
- **Notifications** — for app notifications on newer Android versions
- **Notification listener access** — for notification routing and notification-related automations

Automatic / platform-level app capabilities:
- **Internet**
- **Wake lock**
- **Foreground service**
- **Foreground service data sync**

The app now includes a dedicated **Permissions** screen so users can review what is needed and grant access intentionally.

---

## Privacy and local-first behavior

NativeClaw is built around local execution and local persistence.

Stored on-device:
- chat history
- runtime logs
- prompt templates
- skills and skill packages
- observability traces
- settings and model configuration

Important:
- some optional features such as notification ingestion, push foundations, or Android handoff tools inherently interact with system services or external apps
- Firebase messaging foundations exist in the codebase, but a full backend/cloud registration workflow is still deferred
- privacy characteristics still depend on the model, device, granted permissions, and any external apps/services intentionally connected by the user

---

## Project status

The app already includes:
- functioning Compose app shell
- local persistence
- foreground agent runtime
- LiteRT integration
- model download support
- prompt harness
- skills foundation
- scheduling foundation
- notification routing foundation
- observability and trace persistence

The project is **usable**, but still under active development and validation.

---

## Known limitations / in-progress areas

- native tool coverage is present but still being validated end-to-end on device
- push/FCM support is foundational, not a complete production backend setup
- real-world multimodal behavior depends on the model/runtime combination
- skills/import/export and JS package execution are implemented but still need polish
- some validation work remains around:
  - downloaded-model inference
  - notification access flows
  - scheduled execution reliability
  - real model-driven tool use on device

---

## Why the source is private right now

The code is private temporarily while the project is stabilized and reviewed for a cleaner public release.

Current reasons include:
- continued real-device validation
- hardening tool flows end-to-end
- improving onboarding around model setup and permissions
- cleaning repository contents for public release

This repo exists so the project can still have a public landing page and technical overview without exposing the implementation yet.

---

## Roadmap direction

Near-term priorities:
- finish integrated real-device validation
- polish skills and import/export flows
- harden tool execution reliability
- improve onboarding around model setup and permissions

Longer-term direction:
- stronger skill ecosystem
- better model/runtime compatibility flows
- deeper import/export support
- continued UX and observability improvements

---

## Public release plans

When the project is ready, this repository can be expanded into a full public source release.

Until then, this repository is intentionally limited to documentation only.

---

## License

No license file is currently included in this public repository yet.
Add one before publishing the source publicly if you want clear reuse terms.
