<template>
    <div class="filter-container">

        <!-- Genre-search -->
        <div class="genre-search">

            <label for="genre-select">Filtra per genere</label>
            <select @change="$emit('selectedGenreFilter', genreFilter)" v-model="genreFilter" name="genre-select" id="genre-select">
                <option value="">All</option>
                <option v-for="(element, index) in genres" :key="index" :value="element">{{ element }}</option>
            </select>

        </div>

        <!-- Author-search -->
        <div class="author-search">

            <label for="author-select">Filtra per autore</label>
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
@import '../style/variables.scss';

    .filter-container {
        margin-bottom: 20px;
        display: flex;

        label {
            margin-right: 10px;
            font-family: $primary_text_font;
            font-size: 14px;
            color: $primary_text_color;
        }

        .genre-search,
        .author-search {
            margin-right: 40px;

            select {
                background-color: $primary_color;
                border-color: $primary_color;
                padding: 5px 10px;
                color: $primary_text_color;
                border-radius: 3px;
                
                option {
                    padding: 30px;
                    background-color: $primary_color;
                    color: $primary_text_color;
                }
            }
        }
        
    }
</style>