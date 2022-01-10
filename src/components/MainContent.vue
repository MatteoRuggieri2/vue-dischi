<template>
    <div class="container">
        <SearchFilter />

        <div class="wrapper">
            <SingleCard v-for="(singleAlbum, index) in cardObject" :key="index" :album="singleAlbum" />

        </div>
    </div>
</template>

<script>

import axios from 'axios';
import SearchFilter from "./SearchFilter.vue";
import SingleCard from "./SingleCard.vue";

export default {
    name: 'MainContent',
    components: {
        SingleCard,
        SearchFilter
    },

    data: function() {
        return {
            cardObject: [],
        };
    },

    created: function() {
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
            this.cardObject = response.data.response;
        });
    }
}
</script>

<style lang="scss" scoped>
    .wrapper {
        display: flex;
        flex-wrap: wrap;
        font-family: Arial, Helvetica, sans-serif;
    }
</style>