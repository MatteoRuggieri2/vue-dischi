<template>
    <div class="loading-container">
        <span class="loading-text">Caricamento...</span>
    </div>
</template>

<script>
export default {
    name: 'Loading'
}
</script>

<style lang='scss' scoped>
@import '../style/variables.scss';

    .loading-container {

        .loading-text {
            color: $primary_text_color;
            font-family: $primary_text_font;
            font-size: 18px;
        }
    }

</style>