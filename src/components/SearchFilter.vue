<template>
    <div class="filter-container">

        <!-- Genre-search -->
        <div class="genre-search">

            <select @change="$emit('selectedGenreFilter', genreFilter)" v-model="genreFilter" name="genre-select" id="genre-select">
                <option value="">All</option>
                <option value="rock">Rock</option>
                <option value="pop">Pop</option>
                <option value="jazz">Jazz</option>
                <option value="metal">Metal</option>
            </select>

        </div>

        <!-- Author-search -->
        <div class="author-search">

            <select @change="$emit('selectedAuthorFilter', authorFilter)" v-model="authorFilter" name="author-select" id="author-select">
                <option value="">All</option>
                <option value="Bon Jovi">Bon Jovi</option>
                <option value="Dave Weckl">Dave Weckl</option>
                <option value="Deep Purple">Deep Purple</option>
                <option value="Eric Clapton">Eric Clapton</option>
                <option value="Iron Maiden">Iron Maiden</option>
                <option value="Metallica">Metallica</option>
                <option value="Michael Jacjson">Michael Jacjson</option>
                <option value="Queen">Queen</option>
                <option value="Steve Gadd Band">Steve Gadd Band</option>
                <option value="Sting">Sting</option>

            </select>

        </div>
    </div>
</template>

<script>
export default {
    name: 'SearchFilter',
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