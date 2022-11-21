<script>

import {store} from '../data/store'

export default {
  name: 'AppSearch',
  data(){
    return{
      store
    }
  },
  methods:{
    reset(){
      store.characterToSearch = '';
      store.statusToSearch = '';
      this.$emit('startSearch');
    }
  }
}
</script>
<template>

<div class="container">
  <div class="row justify-content-center py-5" >
    <div class="col-auto">
      <input v-model="store.characterToSearch"  type="text" class="form-control" placeholder="Serach Character">
    </div>
    <div class="col-auto">
      <select v-model="store.statusToSearch" class="form-select">
        <option value="" selected>Select Status</option>
        <option v-for="(status, index) in store.listStatus" :key="index" :value="status">{{status}}</option>
      </select>
    </div>
    <div class="col-auto">
      <button @click="$emit('startSearch')"  class="btn btn-info">Search</button>
    </div>
    <div class="col-auto">
      <button @click="reset()" class="btn btn-warning">Reset</button>
    </div>
  </div>
</div>
  
</template>


<style lang="scss" scoped>

</style>