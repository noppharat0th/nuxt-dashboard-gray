<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const items = ref<NavigationMenuItem[][]>([
  [
    {
      label: 'Guide',
      icon: 'i-lucide-book-open',
      active: true,
    },
    {
      label: 'Composables',
      icon: 'i-lucide-database',
    },
    {
      label: 'Components',
      icon: 'i-lucide-box',
      to: '/docs/components',
    }
  ],
])
</script>

<template>
  <UNavigationMenu
    highlight
    highlight-color="primary"
    orientation="horizontal"
    :items="items"
    class="data-[orientation=horizontal]:border-b border-default data-[orientation=horizontal]:w-full data-[orientation=vertical]:w-48"
  />
</template>
