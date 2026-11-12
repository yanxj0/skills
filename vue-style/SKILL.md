---
name: vue-style
description: Create or edit Vue 3 components in this EMC Analyzer project using its Composition API, SFC, styling, and component organization conventions.
---

# Vue Style

Use this skill when creating or changing Vue components and views in this repository.

## Project conventions

- Use Vue 3 single-file components and `<script setup>` with the Composition API.
- Follow the nearby component's section order, generally `<template>`, `<script setup>`, then `<style>`.
- Use `defineProps`, `computed`, and other Vue APIs to express component inputs and derived state. Keep component logic close to the UI unless it is reusable or substantial enough to belong in `src/utils/hooks`.
- Use Pinia for shared application state, following existing stores in `src/stores`.
- Keep API access in `src/api`; use existing request helpers and established response handling.
- Place page-level views under `src/views` and reusable UI under `src/components` or the relevant view's `components` directory. Follow the existing `index.vue` convention for directory entry components.
- Prefer the project's existing Tailwind utilities for straightforward layout and styling. Use SCSS for styles that benefit from nesting, pseudo-elements, or component-specific rules; use `scoped` when styles should remain component-local.
- Use single quotes and omit semicolons in script code, consistent with Oxfmt configuration.
- Use business-meaningful component, prop, and state names. Follow nearby files for casing and event conventions.

## Implementation guidance

- Keep templates readable and declarative. Move nontrivial calculations and reusable behavior into computed values or composition functions rather than embedding complex expressions in markup.
- Preserve existing loading, empty, error, and interaction behavior when modifying a component.
- Reuse existing components and project dependencies when they fit; avoid introducing a new abstraction for a one-off, simple case.
- Keep styling and logic changes focused. Match the local component patterns and avoid unrelated formatting or layout changes.
