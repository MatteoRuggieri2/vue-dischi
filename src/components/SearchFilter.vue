<template>
    <div class="filter-container">

        <!-- Genre-search -->
        <div class="genre-search">

            <select @change="$emit('selectedGenreFilter', genreFilter)" v-model="genreFilter" name="genre-select" id="genre-select">
                <option value="">All</option>
                <option v-for="(element, index) in genres" :key="index" :value="element">{{ element }}</option>
            </select>

        </div>

        <!-- Author-search -->
        <div class="author-search">

            <select @change="$emit('selectedAuthorFilter', authorFilter)" v-model="authorFilter" name="author-select" id="author-select">
                <option value="">All</option>
                <option v-for="(element, index) in authors" :key="index" :value="element">{{ element }}</option>
            </select>

        </div>
    </div>
</template>

<script>
export default {
    name: 'SearchFilter',
    props: ["authors", "genres"],
    data: function() {
        return {
            genreFilter: '',
            authorFilter: ''
        };
    },
}
</script>

<style lang="scss" scoped>
    .filter-container {
        margin-bottom: 20px;
        display: flex;

        .genre-search {
            margin-right: 10px;
        }
    }
</style>