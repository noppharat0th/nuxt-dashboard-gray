<template>
    <div class="grid grid-cols-2 gap-5">
        <Card>
            <ToPoJson />
        </Card>
        <Card>
            <Vertical />
        </Card>
    </div>
</template>

<script setup lang="ts">
import ToPoJson from '~/components/chart/ToPoJson.vue';
import Vertical from '~/components/chart/Vertical.vue';
import Card from '~/components/ui/card.vue';
</script>

<style lang="scss" scoped></style>