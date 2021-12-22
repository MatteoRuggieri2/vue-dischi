<template>
    <div class="container">
        <div class="wrapper">
            <SingleCard v-for="(singleAlbum, index) in cardObject" :key="index" :album="singleAlbum" />

        </div>
    </div>
</template>

<script>

import axios from 'axios';
import SingleCard from "./SingleCard.vue";

export default {
    name: 'MainContent',
    components: {
        SingleCard,
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
            console.log('cardObject', this.cardObject) // DA RIMUOVERE     DA RIMUOVERE     DA RIMUOVERE
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