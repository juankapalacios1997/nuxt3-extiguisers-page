<template>
    <div>
        <h3>Customer reviews</h3>
        <div v-if="reviewers.length">
            <ReviewCard v-for="review in reviewers"
            :review="review"
            />
        </div>
        <div v-else>
            ...Loading
        </div>
    </div>
</template>
<script setup lang="ts">
const reviewers = ref<any[]>([]);

const websiteStore = useWebsiteStore();

const executeFetchUsersReviews = async () => {
    await websiteStore.fetchUsersReviews();

    reviewers.value = websiteStore.getUserReviews;
}

onMounted(async () => {
    executeFetchUsersReviews();
})

</script>