<template>
    <ul>
        <li> <img :src="'https://image.tmdb.org/t/p/w92/'+ film.poster_path" alt=""></li>

        <li v-if="film.title != undefined">{{film.title}}</li>
        <li v-else> {{film.name}}</li>

        <li v-if="film.original_title != undefined">{{film.original_title}}</li>
        <li v-else> {{film.original_name}} </li>

        <li>
            <img class="language-flag-style" :src="require(`../../assets/img/flags/${film.original_language}.png`)" alt="">
        </li>

        <li>{{film.vote_average}}</li>
    </ul>
</template>

<script>
export default {
    name: "Catalogo-richiesto",
    props: {
        'film': Object
    },
}
</script>

<style lang="scss" scoped>
    .language-flag-style{
        width: 25px;
    }
</style>