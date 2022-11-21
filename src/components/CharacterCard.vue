<script>


export default {
  name: 'CharacterCard',
  data(){
    return{
      
    }
  },
  props:{
    character: Object
  }
}
</script>
<template>
<!-- name status species image -->
  <div class="sc-card col-3" >
    <img :src="character.image" :alt="character.name">
    <h4>{{character.name}}</h4>
    <p>{{character.status}}</p>
    <p>{{character.species}}</p>
  </div>
  
</template>


<style lang="scss" scoped>

@use '../styles/partials/vars' as *;

.sc-card{
  text-align: center;
  margin-bottom: 50px;
  img{
    max-width: 100%;
    border-radius: 50%;
    box-shadow: 0 0 5px 3px rgba( #000000, .15);
    transition: all .2s;
    margin-bottom: 20px;
    &:hover{
      transform: scale(1.05);
    }
  }
  h4{
    text-transform: capitalize;
    &::after{
      content: '';
      display: block;
      border-bottom: 1px solid $primary-color;
      width: 50px;
      margin: 1rem auto;
    }
  }
}
</style>