# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-page Uzbek-language (Latin script) investor landing site for **AgroConnect**, a four-sided agricultural marketplace concept (fermerlar / xaridorlar / haydovchilar / yuk ortuvchilar) for Uzbekistan. Static site, no build system, no package manager, no tests.

All financial figures are in **soum (UZS)** — `trln so'm` / `mlrd so'm` / `mln so'm` / `ming so'm`. USD figures should not appear on the page; use them only as comparison context in private notes if needed. Comma is the decimal separator (e.g. `444,6 trln so'm`).

## Structure

The site is one file: [index.html](index.html). All CSS lives in a `<style>` block in `<head>`; all JS (smooth-scroll, form stub, Chart.js setup) lives in one `<script>` block at the end of `<body>`. [mardon.JPG](mardon.JPG) is the founder photo (currently unreferenced after the redesign — the Team section was removed; keep the file unless asked to delete it).

Companion docs (markdown, not loaded by the page): [MARKET_ANALYSIS.md](MARKET_ANALYSIS.md) holds the TAM/SAM/SOM logic and ecosystem/monetization model that the landing page numbers reference; [TECHNICAL_SPEC.md](TECHNICAL_SPEC.md) is the TZ (stack, schema, API, flows). Keep these aligned with the figures on the page when editing.

Tailwind is loaded via the Play CDN. Tailwind config is **inlined** in a `<script>` block before page content — it extends the theme with custom `ink`, `moss` color palettes and `Inter` / `JetBrains Mono` fonts. Charts use Chart.js via CDN (`chart.js@4.4.0`); three canvases (`#tamChart`, `#growthChart`, `#revenueChart`) are wired in the inline script.

Section IDs (and the nav anchors that target them): `#problem`, `#how`, `#market`, `#features`, `#pricing`, `#cta`. Renaming any of these requires updating both the `<a href="#...">` and any in-page CTAs that link to it.

## Running locally

Open `index.html` directly in a browser, or serve the directory statically (e.g. `python -m http.server` or VS Code Live Server). No build step.

## Conventions

- Page copy is Uzbek (Latin). The TZ supports UZ-Latin / UZ-Cyrillic / RU as a future i18n surface but the marketing site itself is single-locale.
- The CTA form (`#ctaForm`) is a stub — its submit handler swaps the button to "Yuborildi ✓" and resets after ~2.4s. There is no backend.
- All headline numbers (TAM 355 trln so'm, sectoral loss 42 trln so'm, 4,8 mln producers, ~55 mlrd so'm Y3 ARR, etc.) trace to [MARKET_ANALYSIS.md](MARKET_ANALYSIS.md), which in turn cites stat.uz / cbu.uz / gazeta.uz. If you change a figure on the page, update the doc, and vice versa.
- Charts read inline data arrays in the `<script>` block (no external JSON). The `fmtSoum(mlrd)` helper formats values in mlrd → trln so'm with comma decimals — reuse it for any new chart. Year arrays in `growthChart` must stay length-5 (Y1–Y5) and aligned with the projection table in the market doc.
- When changing the USD/UZS exchange rate basis, also revisit `growthChart` and `revenueChart` data arrays — the page does not convert at render time; figures are pre-baked in soums.
