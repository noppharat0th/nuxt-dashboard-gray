<script setup lang="ts">
import type { DropdownMenuItem, NavigationMenuItem, SidebarProps } from '@nuxt/ui'
defineProps<Pick<SidebarProps, 'variant' | 'collapsible' | 'side'>>()

const open = ref(true)

const colorMode = useColorMode()

const teams = ref([
    {
        label: 'Nuxt',
        avatar: {
            src: 'https://github.com/nuxt.png',
            alt: 'Nuxt'
        }
    },
    {
        label: 'Vue',
        avatar: {
            src: 'https://github.com/vuejs.png',
            alt: 'Vue'
        }
    },
    {
        label: 'UnJS',
        avatar: {
            src: 'https://github.com/unjs.png',
            alt: 'UnJS'
        }
    }
])
const selectedTeam = ref(teams.value[0])

const teamsItems = computed<DropdownMenuItem[][]>(() => {
    return [
        teams.value.map((team, index) => ({
            ...team,
            kbds: ['meta', String(index + 1)],
            onSelect() {
                selectedTeam.value = team
            }
        })),
        [
            {
                label: 'Create team',
                icon: 'i-lucide-circle-plus'
            }
        ]
    ]
})

function getItems(state: 'collapsed' | 'expanded') {
    return [
        {
            label: 'Inbox',
            icon: 'i-lucide-inbox',
            badge: '4'
        },
        {
            label: 'Issues',
            icon: 'i-lucide-square-dot'
        },
        {
            label: 'Activity',
            icon: 'i-lucide-square-activity'
        },
    ] satisfies NavigationMenuItem[]
}

const user = ref({
    name: 'Benjamin Canac',
    avatar: {
        src: 'https://github.com/benjamincanac.png',
        alt: 'Benjamin Canac'
    }
})

const userItems = computed<DropdownMenuItem[][]>(() => [
    [
        {
            label: 'Profile',
            icon: 'i-lucide-user'
        },
        {
            label: 'Billing',
            icon: 'i-lucide-credit-card'
        },
        {
            label: 'Settings',
            icon: 'i-lucide-settings',
            to: '/settings'
        }
    ],
    [
        {
            label: 'GitHub',
            icon: 'i-simple-icons-github',
            to: 'https://github.com/nuxt/ui',
            target: '_blank'
        },
        {
            label: 'Log out',
            icon: 'i-lucide-log-out'
        }
    ]
])

defineShortcuts(extractShortcuts(teamsItems.value))
</script>

<template>
    <div class="flex flex-1">
        <USidebar v-model:open="open" variant="inset" collapsible="icon" rail :ui="{
            container: 'h-full',
            inner: 'divide-transparent',
            body: 'py-0'
        }">
            <template #header>
                <UDropdownMenu :items="teamsItems" :content="{ align: 'start', collisionPadding: 12 }"
                    :ui="{ content: 'w-(--reka-dropdown-menu-trigger-width) min-w-48' }">
                    <UButton v-bind="selectedTeam" trailing-icon="i-lucide-chevrons-up-down" color="neutral"
                        variant="ghost" square class="w-full data-[state=open]:bg-elevated overflow-hidden" :ui="{
                            trailingIcon: 'text-dimmed ms-auto'
                        }" />
                </UDropdownMenu>
            </template>

            <template #default="{ state }">
                <UNavigationMenu :key="state" :items="getItems(state)" orientation="vertical"
                    :ui="{ link: 'p-1.5 overflow-hidden' }" />
            </template>

            <template #footer>
                <UDropdownMenu :items="userItems" :content="{ align: 'center', collisionPadding: 12 }"
                    :ui="{ content: 'w-(--reka-dropdown-menu-trigger-width) min-w-48' }">
                    <UButton v-bind="user" :label="user?.name" trailing-icon="i-lucide-chevrons-up-down" color="neutral"
                        variant="ghost" square class="w-full data-[state=open]:bg-elevated overflow-hidden" :ui="{
                            trailingIcon: 'text-dimmed ms-auto'
                        }" />
                </UDropdownMenu>
            </template>
        </USidebar>

        <!-- Content -->
        <slot></slot>
        
    </div>
</template>
