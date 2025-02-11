<template>
  <div class="container">
    <Hero />
    <LargeCardDisplay 
    v-for="section, i in largeCardInfo"
    :key="section.id"
    :section="section"
    :is-first="i === 0"
    />
    <SmallCardDisplay v-for="section in smallCardInfo"
    :key="section.id"
    :section="section"
    />
  </div>
</template>
<script setup lang="ts">
import { largeCardSections, smallCardSections } from "~/assets/data";
import SmallCardDisplay from "../components/SmallCardDisplay.vue";

const largeCardInfo = ref(largeCardSections);
const smallCardInfo = ref(smallCardSections);
</script>