<template>
  <div v-for="post in posts" :key="post.id">
    <SinglePost :post="post"></SinglePost>
</div>
</template>

<script>
import { onMounted, onUnmounted, onUpdated } from '@vue/runtime-core'

import SinglePost from './SinglePost'
export default {
  components: { SinglePost },
    props:["posts"],
    setup(){
        onMounted(()=>{console.log("Data is Mounted")});
        onUnmounted(()=>{console.log("Data is Unmounted")});
        onUpdated(()=>{console.log("Data is updated")});
    }
}
</script>

<style>

</style>