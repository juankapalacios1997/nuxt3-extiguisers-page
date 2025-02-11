<template>
    <div class="review-card">
        <div class="image-container">
            <img :src="props.review.picture" alt="">
        </div>
        <div class="text-container" >
            <h6>{{ props.review.username }}</h6>
            <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Repellendus quam magni beatae possimus debitis.</p>
        </div>
    </div>
</template>

<script setup lang="ts">
    interface ReviewType {
        id: string,
        name: string,
        username: string,
        picture: string
    }

    const props = defineProps({
        review: {
            type: [Object] as PropType<ReviewType>,
            required: true,
        }
    })

</script>

<style scoped>
    .review-card {
        margin-top: 1.5rem;
        height: 4rem;
        display: flex;
    }
    .text-container {
        margin-left: 2rem
    }
    img {
        width: 4rem;
        height: 4rem;
        border-radius: 100%;
    }
    p {
        color: grey
    }
</style>