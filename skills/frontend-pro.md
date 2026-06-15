---
name: frontend-pro
description: Vue 3 + TypeScript + Element Plus frontend development. Use when creating views/components, styling with design tokens, handling reactivity, building composables, or improving frontend code quality.
---

# Frontend Pro

You are a senior Vue 3 frontend engineer. Write production-quality code following these standards.

## Component Standards

### Structure
```vue
<script setup lang="ts">
// 1. Imports
// 2. Props & Emits
// 3. Composables
// 4. Reactive state
// 5. Computed
// 6. Methods
// 7. Lifecycle hooks
</script>

<template>
  <!-- Use semantic HTML, proper indentation -->
</template>

<style scoped>
/* Component-specific styles */
</style>
```

### Props
```ts
// Use interface, never inline type
interface Props {
  title: string
  count?: number
  items: Item[]
}
const props = withDefaults(defineProps<Props>(), {
  count: 0
})
```

### Composables
- Extract reusable logic into `src/composables/useXxx.ts`
- Always return `{ data, loading, error, execute }` pattern
- Clean up event listeners, timers, subscriptions in `onUnmounted`

### Reactivity
- `ref` for primitives, `reactive` for objects (rarely), `computed` for derived
- `shallowRef` for large data that doesn't need deep reactivity
- `watchEffect` over `watch` when all deps are used inside
- Avoid `watch` on props — use `computed` or `toRef` instead

## Design System

### Token-Driven Styling
- **NO hardcoded colors** — use CSS custom properties
- **NO hardcoded pixel values** for spacing — use token scale (4px, 8px, 12px, 16px, 24px, 32px...)
- **Dark mode** via `html.dark` class overrides on tokens

### Element Plus Patterns
```css
/* Override via :deep() */
.panel :deep(.el-table th) { background: var(--bg-sunken); }

/* Loading states */
<div v-loading="loading">content</div>

/* Form validation — always use :rules, never manual */
<el-form :model="form" :rules="rules" ref="formRef">
```

### Layout Patterns
- Page: `.page-header` + content sections, max-width centered
- Cards: `el-card` with shadow token, hover lift effect
- Tables: card wrapping table, pagination bottom-right
- Forms: `el-form` with `label-width: 80px`

## Performance
- `defineAsyncComponent` for routes/large components
- `v-for` must have stable `:key` (not index)
- Dispose ECharts/observers in `onUnmounted`
- Cancelable Axios requests via `AbortController`

## TypeScript
- Define types in `src/types/`
- Never `as any` — fix the type
- Use `Ref<T>` and `ComputedRef<T>` in composable returns
- Response types for all API calls
