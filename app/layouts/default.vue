<template>
    <Sidebar>
        <!-- Layout Content -->
        <div
            class="flex-1 bg-elevated/25 flex flex-col overflow-hidden lg:peer-data-[variant=inset]:my-4 peer-data-[variant=inset]:m-4 lg:peer-data-[variant=inset]:not-peer-data-[collapsible=offcanvas]:ms-0 peer-data-[variant=inset]:rounded-xl peer-data-[variant=inset]:shadow-sm peer-data-[variant=inset]:ring peer-data-[variant=inset]:ring-default bg-default">
            <div class="h-(--ui-header-height) shrink-0 flex items-center px-4" :class="[
                variant !== 'inset' && 'border-b border-default',
                side === 'right' && 'justify-end'
            ]">
                <UButton :icon="side === 'left' ? 'i-lucide-panel-left' : 'i-lucide-panel-right'" color="neutral"
                    variant="ghost" aria-label="Toggle sidebar" @click="open = !open" />
            </div>

            <div class="flex-1 p-4">
                <TabMenu class="mb-3"/>
                <slot></slot>
            </div>
        </div>

    </Sidebar>
</template>

<script setup lang="ts">
import Sidebar from '~/components/layouts/sidebar.vue';

import type { DropdownMenuItem, NavigationMenuItem, SidebarProps } from '@nuxt/ui'
import TabMenu from '~/components/layouts/tab-menu.vue';
defineProps<Pick<SidebarProps, 'variant' | 'collapsible' | 'side'>>()
const open = ref(true)

</script>

<style scoped></style>