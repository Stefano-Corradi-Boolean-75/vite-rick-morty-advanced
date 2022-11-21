<script>
export default {
  name: 'AppHeader',
  props:{
    title: String
  }
}
</script>
<template>

<div class="container py-3 text-center">
  <h1>{{title}}</h1>
</div>
  
</template>


<style lang="scss" scoped>
h1{
  font-weight: 700;
}

</style>