<template>
    <div class="col-3 my-3 d-flex film-card">
        <div class="film-container">
            <div class="film-poster">
                <div v-if="film.poster_path != null">
                    <img :src="'https://image.tmdb.org/t/p/w342/'+ film.poster_path" alt="">
                </div>
                <div v-else>
                    <img src="https://www.omil.it/images/no_image.png" alt="">
                </div>
            </div>

            <div class="film-info">
                <div v-if="film.title != undefined">TITOLO: {{film.title}}</div>
                <div v-else>TITOLO:{{film.name}}</div>

                <div v-if="film.original_title != undefined">TITOLO-ORIGINALE:{{film.original_title}}</div>
                <div v-else>TITOLO-ORIGINALE: {{film.original_name}} </div>

                <div>
                    LINGUA:
                    <img class="language-flag-style" :src="require(`../../assets/img/flags/${film.original_language}.png`)" alt="">
                </div>
                <div>
                    SCORE:
                    <i v-for="(elemento, index) in film.voto_arrotondato" :key="'fullstar-'+ elemento + index" class="fas fa-star"></i>
                    <i v-for="(elemento, index) in (5 - film.voto_arrotondato) " :key="'emptystar-'+ elemento + index" class="far fa-star"></i>                
                </div>
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
        color: white;
        background-color: black;
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
            border: 3px white solid;
            height: 456px;

            .fa-star{
                color: gold;
            }

        }
    }
</style>