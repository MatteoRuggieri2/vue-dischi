<template>
    <div class="single-album-container">

        <!-- Se il poster non è raggiungibile renderizzo un'immagine alternativa -->
        <object class="album-image" :data="album.poster">
            <img class="album-image" src="../assets/img/poster-not-found.png" />
        </object>
        
        <h2 class="album-title">{{ album.title }}</h2>
        <h3 class="album-author">{{ album.author }}</h3>
    </div>
</template>

<script>
export default {
    name: 'SingleCard',
    props: {
        album: Object
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';
    
    .single-album-container {
        width: calc( (100% / 5) - 40px );
        margin: 0 20px 20px;
        padding: 20px;
        text-align: center;
        background-color: $primary_color;
        cursor: pointer;
        

        .album-image {
            margin-bottom: 20px;
            max-width: 100%;
        }

        .album-title {
            color: $primary_text_color;
            text-transform: uppercase;
            margin-bottom: 20px;
            // font-size: 23px;
            font-size: 1.2vw;
        }

        .album-author {
            color: $secondary_text_color;
            // font-size: 18px;
            font-size: 0.9vw;
            font-weight: lighter;
        }
    }

</style>