<template>
    <header>
        <div class="logo-container">
            <img src="../assets/img/spotify-logo.png" alt="Spotify Logo">
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header'
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';
    header {
        background-color: $primary_color;
        height: 50px;
        display: flex;
        align-items: center;

        .logo-container {
            width: 30px;
            margin: 0 20px;
        }
    }

</style>