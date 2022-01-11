<template>
    <div class="container">
        <SearchFilter @selectedGenreFilter="filterForGenreResearch" @selectedAuthorFilter="filterForAuthorResearch" :authors="authorsArray" :genres="genresArray" />

        <div v-if="(!apiLoading)">

            <div v-if="(filteredResearch.length > 0)" class="wrapper">
                <SingleCard v-for="(singleAlbum, index) in filteredResearch" :key="index" :album="singleAlbum" />
             </div>

            <div v-else-if="(filteredResearch.length === 0)">
                <span class="no-result-text">La ricerca non ha prodotto risultati. Riprova modificando i filtri.</span>
            </div>

        </div>

        <div v-else>
            <Loading />
        </div>
    </div>
</template>

<script>

import axios from 'axios';
import SearchFilter from "./SearchFilter.vue";
import SingleCard from "./SingleCard.vue";
import Loading from "./Loading.vue";

export default {
    name: 'MainContent',
    components: {
        SingleCard,
        SearchFilter,
        Loading
    },

    data: function() {
        return {
            cardObject: [],
            selectedGenreFilter: '',
            selectedAuthorFilter: '',
            authorsArray: [],
            genresArray: [],
            apiLoading: true
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
            
            // Questo serve per non inserire più volte lo stesso autore e
            // per non inserire più volte lo stesso genere
            this.cardObject.forEach((element) => {
                if( !this.authorsArray.includes(element.author) ) {
                    this.authorsArray.push(element.author);
                }

                if( !this.genresArray.includes(element.genre) ) {
                    this.genresArray.push(element.genre);
                }
            });

            this.apiLoading = false;

        });
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

    .wrapper {
        display: flex;
        flex-wrap: wrap;
        font-family: $primary_text_font;
    }

    .no-result-text {
        display: inline-block;
        margin: 40px 0;
        color: $primary_text_color;
        font-family: $primary_text_font;
        font-size: 30px;
    }
</style>