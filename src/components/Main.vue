<template>
  <div>
      <div class="container">
          <div class="row">
              <Ricerca-utente
              @filtra="catalogoScelto"/>
          </div>
          <div class="row mt-5">
              <div class="col">
                <Catalogo-richiesto 
                v-for="(element, index) in rispostaApi"
                :key="index"
                :film=element />
              </div>
          </div>
      </div>
  </div>
</template>

<script>
import CatalogoRichiesto from './sub-components/Catalogo-richiesto.vue'
import axios from 'axios'
import RicercaUtente from './sub-components/Ricerca-utente.vue'

export default {
    components: { 
        CatalogoRichiesto,
        RicercaUtente 
        },
    name: "Main",
    data(){
        return{
            ricercaUtente: "",
            rispostaApi: [],
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
                this.rispostaApi = response.data.results;
                console.log(this.rispostaApi);
            })
            .catch(function (error) {
                console.log(error);
            }); 
          
        },
        catalogoScelto(inputUtente){
            this.ricercaUtente = inputUtente;
            console.log(this.ricercaUtente);
            this.getCatalogo();
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/globals.scss';

</style>