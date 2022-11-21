
<script>

import {store} from '../data/store'

export default {
  name: 'ResultSearch',
  data(){
    return{
      store
    }
  },
  computed:{
    // la computed è una funzione che viene scatenata solo quando un dato reattivo al suo in terno cambia
    // deve avere il return
    outputResult(){
      if(store.charactersListData.length > 0){
        return 'Risultati trovati: ' +  store.charactersListData.length;
      }
      return "Nessun risultato"
    }
  }
}
</script>
<template>
  <div class="container">
    <p class="text-center py-5">{{outputResult}}</p>
  </div>
</template>

<style>

</style>