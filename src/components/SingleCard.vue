<template>
    <div class="single-album-container">
        <img class="album-image" :src="album.poster" :alt="album.title">
        <h2 class="album-title">{{ album.title }}</h2>
        <h3 class="album-author">{{ album.author }}</h3>
    </div>
</template>

<script>
export default {
    name: 'SingleCard',
    props: ['album']
}
</script>

<style lang="scss" scoped>
    
    .single-album-container {
        width: calc( (100% / 5) - 40px );
        margin: 0 20px 20px;
        padding: 20px;
        text-align: center;
        background-color: #2e3a46;

        .album-image {
            margin-bottom: 20px;
        }

        .album-title {
            color: white;
            text-transform: uppercase;
            margin-bottom: 20px;
            font-size: 25px;
        }

        .album-author {
            color: gray;
            font-size: 18px;
        }
    }

</style>