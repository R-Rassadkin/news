<template>

<div class="header">
    <h2 class="header__title">НОВОСТИ</h2>
    <h1 class="header__data">{{now}}</h1>
</div>

    
 </template>

<script>

 export default {
  name: 'App',
  data(){
    return{
      now:new Date().toLocaleDateString(),
      
    }
  },
  
}
</script>

<style scoped lang="scss">
.header{
    background: rgb(32, 122, 150);
    &__title{
        color: rgb(19, 19, 19);
        padding:30px 0 30px 0
    }
    &__data{
        color: rgb(122, 9, 9);
        padding-bottom: 20px;
    }
}

</style>