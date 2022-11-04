<template>
  
  <div class="home">
    <div v-if="posts.length>0">
      <PostList :posts="posts"></PostList>
    </div>
    <div v-else>
      <p>Loading ...</p>
    </div>
    <div v-if="error">
      {{error}}
    </div>

  </div>
</template>

<script>
import PostList from '../components/PostList'
import { ref } from '@vue/reactivity';


export default {
  components: { PostList },
   setup(){
   let posts = ref([]);
   let error = ref("");
   let load = async()=>{
    try{
      let response = await fetch("https://jsonplaceholder.typicode.com/posts");
      
      if(response.status === 404){
        throw new Error ("Not Found URL")
      }
      let datas = await response.json();
      posts.value = datas;
      console.log(datas);
    }catch(abc){
      error.value = abc;
    }
   }

   load();
   return{posts,error}
   }
   
}
</script>

<style>
  
 
</style>
