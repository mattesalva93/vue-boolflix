<template>
    <div class="col-3 my-3 d-flex film-card">
        <div class="film-container">
            <div class="film-poster">
                <div v-if="film.poster_path != null">
                    <img :src="'https://image.tmdb.org/t/p/w342/'+ film.poster_path" alt="">
                </div>
                <div v-else>
                    <img src="../../assets/img/flags/none.png" alt="">
                </div>
            </div>

            <div class="film-info">
                <div v-if="film.title != undefined">TITOLO: {{film.title}}</div>
                <div v-else>TITOLO:{{film.name}}</div>

                <div v-if="film.original_title != undefined">TITOLO-ORIGINALE:{{film.original_title}}</div>
                <div v-else>TITOLO-ORIGINALE: {{film.original_name}} </div>

                <div>
                    <img class="language-flag-style" :src="require(`../../assets/img/flags/${film.original_language}.png`)" alt="">
                </div>

                <div v-if ="film.vote_average == 0">SCORE: &#9734; &#9734; &#9734; &#9734; &#9734; </div>
                <div v-else-if ="film.vote_average == 1">SCORE: &#9733; &#9734; &#9734; &#9734; &#9734; </div>
                <div v-else-if ="film.vote_average == 2">SCORE: &#9733; &#9733; &#9734; &#9734; &#9734; </div>
                <div v-else-if ="film.vote_average == 3">SCORE: &#9733; &#9733; &#9733; &#9734; &#9734; </div>
                <div v-else-if ="film.vote_average == 4">SCORE: &#9733; &#9733; &#9733; &#9733; &#9734; </div>
                <div v-else>SCORE: &#9733; &#9733; &#9733; &#9733; &#9733; </div>
            </div>
        </div>
    </div>

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
    .film-container{
        background-color: white;
        height: 456px;
        width: 100%;
        &:hover .film-poster{
            display: none;
        }
        &:hover .film-info{
            display: flex;
            flex-direction: column;
            justify-content: center;
            div{
                height: 100px;
            }
        }
    }
    .film-card{
        width: 100%;
        height: 100%;
        .film-poster{
            width:100%;
            height: 100%;
            &:hover{
                opacity: 0;
            }
            img{
                height: 456px;
                width: 100%;
                border: 3px white solid;
                object-fit: cover;
            }
        }
        .film-info{
            display: none;

        }
    }
</style>