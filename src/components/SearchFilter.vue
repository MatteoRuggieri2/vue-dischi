<template>
    <div class="filter-container">

        <!-- Genre-search -->
        <div class="genre-search">

            <select @change="$emit('selectedFilter', genreFilter)" v-model="genreFilter" name="" id="">
                <option value="">All</option>
                <option value="rock">rock</option>
                <option value="pop">pop</option>
                <option value="jazz">jazz</option>
                <option value="metal">metal</option>
            </select>

        </div>
    </div>
</template>

<script>
export default {
    name: 'SearchFilter',
    data: function() {
        return {
            genreFilter: ''
        };
    },
}
</script>

<style lang="scss" scoped>
    .filter-container {
        margin-bottom: 20px;

        // test
        background-color: cadetblue;
    }
</style>