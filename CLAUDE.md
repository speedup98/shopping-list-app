# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file Korean-language shopping list web app (`index.html`). No build tools, no dependencies — open directly in a browser.

## Architecture

- **Single HTML file** containing all HTML, CSS (`<style>`), and JS (`<script>`)
- **localStorage** for persistence (`shopping-list` key), storing a JSON array of `{ name: string, checked: boolean, category: string }`
- Vanilla JS with direct DOM rendering via `innerHTML` — `render()` is the sole render function, called after every state change
- XSS protection via `escapeHtml()` for user input
- **Categories**: items are grouped by category (`CATEGORIES` array with `id`, `name`, `icon`). Category filter buttons appear dynamically based on which categories have items.
- **State flow**: user action → `load()` from localStorage → mutate array → `save()` → `render()`. No in-memory cache; every operation round-trips through localStorage.

## Running

Open `index.html` in any browser. No server required.

## Conventions

- UI text is in Korean (한국어)
- Keep everything in the single `index.html` file — do not split into separate CSS/JS files
