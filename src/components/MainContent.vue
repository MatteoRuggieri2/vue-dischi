<template>
    <div class="container">
        <SearchFilter @selectedGenreFilter="filterForGenreResearch" @selectedAuthorFilter="filterForAuthorResearch" :authors="authorsArray" />

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
            selectedAuthorFilter: '',
            authorsArray: []
        };
    },

    methods: {
        filterForGenreResearch: function(filter) {
            this.selectedGenreFilter = filter;
        },

        filterForAuthorResearch: function(filter) {
            this.selectedAuthorFilter = filter;
        }
    },

    computed: {
        filteredResearch() {
            if( this.selectedGenreFilter === '' && this.selectedAuthorFilter === '' ) {
                return this.cardObject;
            }

            const filteredAlbums = this.cardObject.filter((element) => {
                return element.genre.toLowerCase().includes(this.selectedGenreFilter.toLowerCase()) && element.author.toLowerCase().includes(this.selectedAuthorFilter.toLowerCase());
            });

            return filteredAlbums;
        }
    },

    created: function() {
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
            this.cardObject = response.data.response;
            
            // Questo seve per non inserire più volte lo stesso autore
            this.cardObject.forEach(element => {
                if( !this.authorsArray.includes(element.author) ) {
                    this.authorsArray.push(element.author);
                }
            });

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