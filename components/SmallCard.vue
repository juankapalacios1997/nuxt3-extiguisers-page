<template>
    <nuxt-link :to="`/products/${currentCardId}`" class="card">
        <img :src="currentImageUrl" alt="fe" class="image">
    </nuxt-link>
</template>
<script setup lang="ts">
    interface SectionType {
        id: number,
        image: string,
    }

    const props = defineProps({
        card: {
            type: [Object] as PropType<SectionType>,
            required: true,
        }
    })

    const currentImageUrl = computed(() => new URL(`../assets/images/${(props.card as SectionType).image}`, import.meta.url).href);

    const currentCardId = computed(() => `${(props.card as SectionType).id}`);
</script>
<style scoped>
    .card {
        width: 100%;
        height: 12rem;
        border: none;
        overflow: hidden;
        padding: 0;
        cursor: pointer;    }
    .image {
        height: 100%;
        border-radius: 0.5rem;
    }
</style>