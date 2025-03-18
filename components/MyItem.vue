<template>
    <div class="item-container">
        <img :src="currentImageUrl(props.item.image)" alt="item">
        <div class="text-container">
            <h4> {{ props.item.title }} </h4>
            <p> {{ props.item.description }} </p>
        </div>
    </div>
</template>

<script setup lang="ts">
    interface MyItemType {
        id: number
        title: string
        snippet: string
        description: string
        image: string
    }
    // export default {
    //     props: ['item']
    // }
    const props = defineProps({
        item: {
            type: [Object] as PropType<MyItemType>,
            required: true,
        }
    })

    const currentImageUrl = (url:string):string => {
        return new URL(`../assets/images/${url}`, import.meta.url).href
    }

</script>

<style scoped>
    .item-container {
        display: flex;
        margin: 3rem 0
    }
    .text-container {
        padding: 0 1rem
    }
    img {
        width: 17.5rem;
        border-radius: 0.5rem;
        height: 11rem
    }
    p {
        font-size: 0.8rem;
        color: grey
    }
</style>