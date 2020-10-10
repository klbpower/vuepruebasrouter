<template>
  <Titulo texto="Título de mi blog" />
  <!--<button @click="consumirAPI">Consumir API JSON Placeholder</button>-->
  <div v-for="item in arrayBlog" :key="item.id">
    {{ item.title }}
  </div>
</template>

<script>
import Titulo from '../components/Titulo'
export default {
  components:{
    Titulo
  },
  data() {
    return {
      arrayBlog: []
    }
  },
  methods:{
   async consumirAPI(){
      try{
        const data  = await fetch('https://jsonplaceholder.typicode.com/posts');
        const array = await data.json();
        console.log(array);
        this.arrayBlog = array;
      }catch(error){
        console.log(error);
      }
    }
  },
  created() {
    this.consumirAPI();
  }
}
</script>

<style>

</style>