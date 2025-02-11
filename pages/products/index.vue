<template>
    <div class="container">
        <LargeCardDisplay 
        v-for="section in largeCardInfo.slice(0, 1)"
        :key="section.id"
        :section="section"
        />
        <SmallCardDisplay 
        v-for="section in smallCardInfo"
        :key="section.id"
        :section="section"
        />
    </div>
</template>
<script>
import { largeCardSections, smallCardSections } from "~/assets/data.js";

export default {
    name: "productsIndex",
    data() {
        return {
            largeCardInfo: largeCardSections,
            smallCardInfo: smallCardSections
        }
    }
}
</script>
<style scoped>
    
</style>