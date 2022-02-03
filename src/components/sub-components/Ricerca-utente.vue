<template>
    <div class="col d-flex justify-content-end align-items-center">
        <input type="text" 
        name="inputUtente" 
        id="ricercaUtente" 
        placeholder="Inserisci il titolo da ricercare"
        v-model.trim="inputText">
        
        <button @click.prevent="$emit('filtra',inputText)"> 
            Cerca
        </button>
    </div>
</template>

<script>
export default {
    name: "Ricerca-utente",
    data(){
        return{
            inputText:"",
        }
    }
}
</script>

<style lang="scss" scoped>

</style>