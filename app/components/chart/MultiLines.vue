<script lang="ts" setup>
defineOptions({
    tags: ['areacharts', 'multiplelines']
})

withDefaults(
    defineProps<{
        showTitle?: boolean
    }>(),
    {
        showTitle: false
    }
)

const colorMode = useColorMode()

interface AreaChartItem {
    date: string
    desktop: number
    mobile: number
}

const categories: ComputedRef<Record<string, BulletLegendItemInterface>>
    = computed(() => ({
        desktop: {
            name: 'Desktop',
            color: '#ffffff'
        },
        mobile: {
            name: 'Mobile',
            color: '#ffffff'
        }
    }))

const AreaChartData: AreaChartItem[] = [
    { date: '2024-04-01', desktop: 75, mobile: 50 },
    { date: '2024-04-02', desktop: 125, mobile: 100 },
    { date: '2024-04-03', desktop: 167, mobile: 120 },
    { date: '2024-04-04', desktop: 260, mobile: 240 },
    { date: '2024-04-05', desktop: 240, mobile: 290 }
]

const xFormatter = (tick: number): string => {
    return `${AreaChartData[tick]?.date}`
}
</script>

<template>
    <div class="mx-auto max-w-3xl space-y-6 rounded-lg" :class="showTitle ? 'p-6' : ''">
        <div class="flex items-center justify-between">
            <div>
                <h3 class="text-lg font-semibold">
                    Bling Last Year
                </h3>
                <p class="text-gray-400">Lorem ipsum dolor sit, amet consectetur adipisicing elit.</p>
            </div>
            <NuxtLink to="/blocks/bar-charts">
                <UButton icon="i-lucide-copy" size="sm" variant="soft" color="neutral" />
            </NuxtLink>
        </div>
        <AreaChart :key="colorMode.value" :data="AreaChartData" :height="300" :categories="categories"
            :y-grid-line="true" :x-formatter="xFormatter" :curve-type="CurveType.MonotoneX"
            :legend-position="LegendPosition.TopRight" :hide-legend="false" />
    </div>
</template>

<style>
:root {
  --vis-axis-grid-color: rgba(231, 231, 231, 0.05) !important; 
}
</style>