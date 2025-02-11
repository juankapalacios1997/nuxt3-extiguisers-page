<template>
    <SingleProduct 
    :product="product"
    />
</template>

<script setup lang="ts">
const websiteStore = useWebsiteStore();

const id = Number(useRoute().params.id);

const productComputedRef = computed(() => websiteStore.getProductById(id));

const product = productComputedRef.value;

</script>