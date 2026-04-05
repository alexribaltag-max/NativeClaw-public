# NativeClaw

NativeClaw is a **local-first Android agent app** focused on **on-device inference**, a **chat-first UX**, **background execution**, **custom system prompts**, **importable skills**, and **runtime observability**.

This public repository is intentionally **README-only** for now.
The full source code currently lives in a **private repository** while the project is still being hardened and validated.

## What NativeClaw aims to provide

- **Local-first execution** with LiteRT-compatible models
- **Private by default** storage for prompts, history, settings, and traces
- **Background-capable runtime** for agent workflows beyond the visible UI
- **Customizable behavior** through prompt layers, skills, and tool contracts
- **Traceable execution** with logs, history, and runtime observability
- **Extensible architecture** for built-in and imported skills

## Current feature direction

NativeClaw is being built around:

- on-device model runtime integration
- persistent chat sessions
- prompt template management
- multimodal input flows
- skill loading and package-backed skills
- scheduled/background triggers
- notification-driven routing foundations
- tool execution support for Android handoff and local actions
- observability and trace persistence

## Project status

NativeClaw is **under active development**.

The app already has a functioning Android foundation, but the codebase is being kept private until:

- real-device validation is further completed
- tool flows are hardened end-to-end
- onboarding is polished
- repository contents are prepared for public release

## Privacy note

NativeClaw is designed with a local-first mindset, but actual privacy characteristics depend on:

- the model being used
- device configuration
- granted Android permissions
- any external services or apps intentionally connected by the user

## Why the source is private right now

The source is private temporarily while the project is stabilized and reviewed for a cleaner public release.

This repo exists so the project can still have a public landing page and overview without exposing the implementation yet.

## Roadmap direction

Near-term priorities:

- finish device validation
- improve reliability of tool and background flows
- polish skill import/export behavior
- improve setup and model onboarding

Longer-term goals:

- stronger skill ecosystem
- broader model/runtime compatibility
- better import/export workflows
- improved observability UX

## Public release plans

When the project is ready, this repository can be expanded or replaced with a public source release.

Until then, this repository is intentionally limited to documentation only.
