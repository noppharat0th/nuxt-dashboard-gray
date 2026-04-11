<template>
    <div class="grid grid-cols-4 mb-3 gap-5">
        <Card v-for="i in 4">
            <div class="flex justify-between items-center">
                <span class="text-gray-400">Active User</span>
                <UBadge variant="subtle" label="+18.2%"/>
            </div>
            <div class="flex-col">
                <h1 class="text-4xl font-bold">2,450</h1>
                <p class="text-sm text-gray-400">Growup bro</p>
            </div>
        </Card>
    </div>
    <div class="grid grid-cols-2 gap-5">
        <Card>
            <MultiLines/>
        </Card>
        <Card>
            <Vertical />
        </Card>
    </div>
    <Card class="mt-5">
        <Table />
    </Card>
</template>

<script setup lang="ts">
import MultiLines from '~/components/chart/MultiLines.vue';
import Vertical from '~/components/chart/Vertical.vue';
import Card from '~/components/ui/card.vue';
import Table from '~/components/ui/table.vue';
</script>

<style lang="scss" scoped></style>