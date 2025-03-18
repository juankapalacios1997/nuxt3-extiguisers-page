<template>
    <div
    v-if="!store.myRentals.length"
    class="container">
        <h1>Your order has no items yet</h1>
    </div>
    <div
    v-else
    class="container">
        <MyItem 
        v-for="item in store.myRentals"
        :key="item.id"
        :item="item"
        />
    </div>
</template>
<script setup lang="ts">
    const store = useWebsiteStore();
    
    definePageMeta({
        layout: 'no-nav'
    })
</script>