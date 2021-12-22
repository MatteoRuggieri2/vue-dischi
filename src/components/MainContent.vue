<template>
    <div class="container">
        <div class="wrapper">
            <SingleCard />
            <SingleCard />
            <SingleCard />
            <SingleCard />
            <SingleCard />
            <SingleCard />
            <SingleCard />
            <SingleCard />
            <SingleCard />
            <SingleCard />
            <SingleCard />
            <SingleCard />

        </div>
    </div>
</template>

<script>
import SingleCard from "./SingleCard.vue"

export default {
    name: 'MainContent',
    components: {
      SingleCard,
  },
}
</script>

<style lang="scss" scoped>
    .wrapper {
        display: flex;
        flex-wrap: wrap;
    }
</style>