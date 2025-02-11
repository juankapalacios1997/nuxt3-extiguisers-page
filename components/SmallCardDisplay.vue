<template>
    <div class="container">
        <h4 class="header">
            {{ props.section.title }}
        </h4>
        <div class="cards-container">
            <SmallCard v-for="card in section.cards"
            :key="card.id"
            :card="card"
            />
        </div>
    </div>
</template>
<script setup lang="ts">
    interface CardsType {
        id: number,
        image: string
    }

    interface SectionType {
        id: number,
        title: string,
        cards: CardsType[],
    }

    const props = defineProps({
        section: {
            type: [Object] as PropType<SectionType>,
            required: true,
        },
    });
</script>
<style scoped>
    .container {
        margin-top: 2rem;
        margin-bottom: 1.2rem;
    }
    .header {
        font-weight: 700;
        font-size: 1.2rem;
    }
    .snippet {
        color: grey;
        margin-bottom: 1.2rem;
    }
    .cards-container {
        display: grid;
        grid-template-columns: auto auto auto auto;
        column-gap: 12px;
        row-gap: 18px;
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