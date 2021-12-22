<template>
    <div class="single-album-container">
        <img class="album-image" src="https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg" alt="Album">
        <h2 class="album-title">title</h2>
        <h3 class="album-author">author</h3>
    </div>
</template>

<script>
export default {
    name: 'SingleCard'
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