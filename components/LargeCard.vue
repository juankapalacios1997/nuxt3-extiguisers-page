<template>
    <nuxt-link :to="`/products/${props.card.id}`" class="card">
        <img :src="currentImageUrl" alt="fe" class="image">
        <h3 class="header">{{ props.card.title }}</h3>
        <p class="snippet">{{ props.card.snippet }}</p>
    </nuxt-link>
</template>

<script setup lang="ts">
    interface SectionType {
        id: number,
        image: string,
        title: string,
        snippet: string
    }

    const props = defineProps({
        card: {
            type: [Object] as PropType<SectionType>,
            required: true,
        }
    })

    const currentImageUrl = computed(() => new URL(`../assets/images/${props.card.image}`, import.meta.url).href);

</script>
<style scoped>
    .card {
        width: 31.5%;
        height: 25rem;
        border: none;
        overflow: hidden;
        padding: 0;
        cursor: pointer;
    }
    .image {
        height: 65%;
        border-radius: 0.5rem;
    }
    .header {
        color: black;
        font-size: 1.15rem;
        margin-top: 0.4rem;
        text-decoration: none;
    }
    .header:hover {
        color: black;
        text-decoration: none;
    }
    .snippet {
        color: grey;
        text-decoration: none;
        text-align: justify;
    }
    .snippet:hover {
        color: grey;
        text-decoration: none;
    }
</style>