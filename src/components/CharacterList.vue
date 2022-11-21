<script>

import {store} from '../data/store'
import CharacterCard from './CharacterCard.vue'
import AppLoading from './AppLoading.vue'

export default {
  name: 'CharacterList',
  components:{
    CharacterCard,
    AppLoading
  },
  data(){
    return{
      store
    }
  }
}
</script>
<template>
  <div class="container h-100">
    <div v-if="store.isLoaded" class="row">
      <CharacterCard 
      v-for="character in store.charactersListData" 
      v-show="character.image != '' "
      :key="character.id"
      :character="character"
       />
    </div>
    <div v-else>
      <AppLoading title="Rick & Morty loading..." />
    </div>
  </div>
  
</template>


<style lang="scss" scoped>

</style>