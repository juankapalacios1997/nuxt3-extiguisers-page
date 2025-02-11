<template>
    <div class="container" :class="{ 'first-container': isFirst }">
        <h4 class="header">
            {{ props.section.title }}
        </h4>
        <p class="snippet">
            {{ props.section.snippet }}
        </p>
        <div class="cards-container">
            <LargeCard v-for="card in section.cards"
            :key="card.id"
            :card="card"
            />
        </div>
    </div>
</template>
<script setup lang="ts">
    interface CardsType {
        id: number,
        title: string,
        snippet: string,
        image: string
    }

    interface SectionType {
        title: string,
        snippet: string
        cards: CardsType[],
    }

    const props = defineProps({
        section: {
            type: [Object] as PropType<SectionType>,
            required: true,
        },
        isFirst: {
            type: Boolean,
            default: false,
        },
    });

</script>
<style scoped>
    .container {
        margin-top: 2rem;
    }
    .header {
        font-weight: 700;
        font-size: 1.5rem;
    }
    .snippet {
        color: grey;
        margin-bottom: 1.5rem;
    }
    .cards-container {
        display: flex;
        justify-content: space-between;
    }

    @media screen and (min-width: 900px) and (max-width: 1799px)  {
        .first-container {
            margin-top: 18rem;
        }
    }

    @media screen and (min-width: 1800px) {
        .first-container {
            margin-top: 12rem;
        }
    }

</style>