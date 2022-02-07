<template>
  <div>
    <header>
        <div class="container">
            <div class="row d-flex justify-content-space-around">
                <div class="col-9 d-flex align-items-center">
                    <h1>Boolflix</h1> 
                </div>
                <Ricerca-utente 
                @filtra="catalogoScelto"/> 
            </div>
        </div>
    </header>
    <main>
      <div class="container">
            <div v-if="caricato != true" class="row d-flex justify-content-space-around">

            </div>
            <div v-else>
                <div class="row d-flex justify-content-space-around">
                    <h1>Movies</h1>
                    <Catalogo-richiesto 
                    v-for="(element, index) in rispostaApiMovie"
                    :key="index"
                    :film=element />
                </div>
                <div class="row d-flex justify-content-space-around">
                    <h1>Series</h1>
                    <Catalogo-richiesto 
                    v-for="(element, index) in rispostaApiTV"
                    :key="index"
                    :film=element />
                </div>
            </div>
      </div>
    </main>
  </div>
</template>

<script>
import CatalogoRichiesto from './sub-components/Catalogo-richiesto.vue'
import RicercaUtente from './sub-components/Ricerca-utente.vue'
import axios from 'axios'

export default {
    components: { 
        CatalogoRichiesto,
        RicercaUtente,
        },
    name: "Main",
    data(){
        return{
            ricercaUtente: "",
            rispostaApiMovie: [],
            rispostaApiTV: [],
            rispostaApi: [],
            caricato: false,
        }
    },
    methods: {
        getCatalogo: function() { 
            axios
            .get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: 'c118f218a2e8045c8dc9d93ebeb85c9b',
                    language: 'it-IT',
                    query: this.ricercaUtente,
                }
            })
            .then( (response) => {
                this.rispostaApiMovie = response.data.results;
                this.rispostaApiMovie.forEach(element => {
                        element.voto_arrotondato = {};
                        return element.voto_arrotondato = this.getStelline(element.vote_average);
                    });
                axios.get('https://api.themoviedb.org/3/search/tv', {
                params: {
                    api_key: 'c118f218a2e8045c8dc9d93ebeb85c9b',
                    language: 'it-IT',
                    query: this.ricercaUtente,
                }
            })
                .then( (response) => {
                    this.rispostaApiTV = response.data.results;
                    this.rispostaApiTV.forEach(element => {
                        element.voto_arrotondato = {};
                        return element.voto_arrotondato = this.getStelline(element.vote_average);
                    });
                    this.caricato = true;
            })
            })
            .catch(function (error) {
                console.log(error);
            }); 
          
        },
        catalogoScelto(inputUtente){
            this.ricercaUtente = inputUtente;
            console.log(this.ricercaUtente);
            this.getCatalogo();
        },
        getStelline(num){
            return Math.ceil((num)/2);
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/globals.scss';
    header{
        width: 100%;
        background-color: black; 
        h1{
            color: red;
            text-transform: uppercase;
        }
    }
    main{
        min-height: calc(100vh - 56px);
        background-color: grey ;
    }

</style>