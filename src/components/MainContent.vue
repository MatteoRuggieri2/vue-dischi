<template>
    <div class="container">
        <SearchFilter @selectedFilter="filterForResearch" />

        <div class="wrapper">
            <SingleCard v-for="(singleAlbum, index) in filteredResearch" :key="index" :album="singleAlbum" />

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
            selectedGenreFilter: '',
        };
    },

    methods: {
        filterForResearch: function(filter) {
            this.selectedGenreFilter = filter;
        }
    },

    computed: {
        filteredResearch() {
            if( this.selectedGenreFilter === '' ) {
                return this.cardObject;
            }

            const filteredAlbums = this.cardObject.filter((element) => {
                return element.genre.toLowerCase().includes(this.selectedGenreFilter.toLowerCase())
            });

            return filteredAlbums;
        }
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