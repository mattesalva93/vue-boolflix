<template>
    <ul>
        <li>{{film.title}}</li>
        <li>{{film.original_title}}</li>

        <li v-if="film.original_language == 'it'"> 
            <img src="../../assets/img/it-flag.png" alt=""> 
        </li>
        <li v-else-if="film.original_language == 'en'"> 
            <img src="../../assets/img/en-flag.png" alt=""> 
        </li>
        <li v-else-if="film.original_language == 'es'"> 
            <img src="../../assets/img/es-flag.png" alt=""> 
        </li>
        <li v-else>
            <img src="../../assets/img/no-flag.png" alt="">
        </li>

        <li>{{film.vote_average}}</li>
    </ul>
</template>

<script>
export default {
    name: "Catalogo-richiesto",
    props: {
        'film': Object
    }
}
</script>

<style lang="scss" scoped>
    img{
        width: 25px;
    }
</style>