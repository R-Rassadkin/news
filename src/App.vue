<template>
<div class="container">
  <h1 class="title">{{now}}</h1>
    <hr>
    <span class="title">открыто:{{openRate}}| прочитано:{{readRate}}</span>
    <hr>
    <news
       v-for="(item,idx) in arr"
      :key="idx"
      :id='item.id'
      :item="item"
      :isOpen="item.isOpen"
      :name='item.name'
      :img="item.src"
      :title="item.title"
      :wasRead='item.wasRead'
      @open-news='openRate++'
      @read-news='readNews'
      @unmark='unMark'
      ></news>

</div>
    
</template>

<script>
import news from './components/news.vue'


export default {
  name: 'App',
  data(){
    return{
      now:new Date().toLocaleDateString(),
      openRate:0,
      readRate:0,
  
      arr:[
        {id:1,
        name:' news 1',
        isOpen:false,
        тsrc:'1.jpg',
        title:'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Earum!',
        wasRead:false},

        {id:2,
        name:'news 2',
        isOpen:false,
        src:'2.jpg',
        title:'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Earum!',
        wasRead:false},

        {id:3,
        name:'news 3',
        isOpen:false,
        src:'3.jpg',
        title:'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Earum!',
        wasRead:false}
      ]
    }
  },
  methods:{
    readNews(id){
      console.log(id);
      this.readRate++
      const idx=this.arr.findIndex(news=>news.id===id)
      this.arr[idx].wasRead=true
    },
    unMark(id){
      this.isOpen=false
      this.readRate--
      const idx=this.arr.findIndex(news=>news.id===id)
      this.arr[idx].wasRead=false
    }
  },
  components: {
    news
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  font-size: 25px;
  font-weight: 900;
}
.container{
  color: azure;
}
.title{
  color: black;
}
body,
h1,
h2,
h3,
h4,
p,
li,
dd {
  margin: 0;
}

</style>
