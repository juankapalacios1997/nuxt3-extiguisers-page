<template>
    <div>
        <nuxt-link class="nav-link nonav-link" to="/"><span class="sr-only">Go Back</span></nuxt-link>
        <slot />
    </div>
</template>

<style scoped>
.nonav-link {
    margin: 0 auto;
    background-color: #F0F0F0;
    padding: 11px 4px;
}
span {
    font-size: 20px;
}
</style>