<template>
    <ul>
        <li v-if="film.poster_path != null"> <img :src="'https://image.tmdb.org/t/p/w92/'+ film.poster_path" alt=""></li>
        <li v-else> <img src="../../assets/img/flags/none.png" alt="" style="height: 138px; width: 92px"></li>

        <li v-if="film.title != undefined">{{film.title}}</li>
        <li v-else> {{film.name}}</li>

        <li v-if="film.original_title != undefined">{{film.original_title}}</li>
        <li v-else> {{film.original_name}} </li>

        <li>
            <img class="language-flag-style" :src="require(`../../assets/img/flags/${film.original_language}.png`)" alt="">
        </li>

        <li v-if ="film.vote_average == 0"> &#9734; &#9734; &#9734; &#9734; &#9734; </li>
        <li v-else-if ="film.vote_average == 1"> &#9733; &#9734; &#9734; &#9734; &#9734; </li>
        <li v-else-if ="film.vote_average == 2"> &#9733; &#9733; &#9734; &#9734; &#9734; </li>
        <li v-else-if ="film.vote_average == 3"> &#9733; &#9733; &#9733; &#9734; &#9734;</li>
        <li v-else-if ="film.vote_average == 4"> &#9733; &#9733; &#9733; &#9733; &#9734;</li>
        <li v-else> &#9733; &#9733; &#9733; &#9733; &#9733; </li>

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