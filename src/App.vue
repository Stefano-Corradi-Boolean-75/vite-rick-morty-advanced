<script>

import axios from 'axios'
import {store} from './data/store'

import AppHeader from './components/AppHeader.vue'
import AppSearch from './components/AppSearch.vue'
import ResultSearch from './components/ResultSearch.vue'
import CharacterList from './components/CharacterList.vue'


export default {
  name: 'App',
  data(){
    return{
      store
    }
  },
  components:{
    AppHeader,
    AppSearch,
    CharacterList,
    ResultSearch
  },
  methods:{
    getCharacters(){
      store.isLoaded = false;
      axios.get(store.apiUrlActive, {
        params:{
          name: store.characterToSearch,
          status: store.statusToSearch
        }
      })
        .then( result => {
          store.charactersListData = result.data.results
          // salvo le info per la paginazione
          store.next = result.data.info.next;
          store.prev = result.data.info.prev;
          // solo alla prima chiamata API salvo gli status presenti
          if(store.listStatus.length === 0){
            store.charactersListData.forEach(char => {
              // se lo statun non è presente lo pusho nella lista globle degli status
              if(!store.listStatus.includes(char.status)) store.listStatus.push(char.status);
            })
          }
          store.isLoaded = true;
        })
        .catch( error => {
          store.charactersListData = [];
          store.next = null;
          store.prev = null;
          store.isLoaded = true;
          //console.log(error)
        })
      },
      gotoPage(direction){
        store.apiUrlActive = store[direction] // sotre.next oppure store.prev
        this.getCharacters();
      },
      startSearch(){
        store.apiUrlActive = store.apiUrl;
        this.getCharacters();
      }
  },
  mounted(){
    this.getCharacters();    
  }
}
</script>

<template>
  
    <AppHeader title="Rick & Morty App" />
  
  <main>
    <AppSearch @startSearch="startSearch()"  />
    <CharacterList />
    <ResultSearch />
    <div class="container pb-3 text-center">
      <button @click="gotoPage('prev')" v-if="store.prev" class="btn btn-secondary me-3">prev</button>
      <button @click="gotoPage('next')" v-if="store.next" class="btn btn-secondary">next</button>
    </div>
  </main>

</template>


<style lang="scss">

@use './styles/general';

</style>