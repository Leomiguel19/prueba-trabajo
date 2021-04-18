<template>
  <div class="home">
    <h2>Welcome to my application</h2>
    <h2>{{name}}</h2>
  </div>
</template>

<script>
//import HelloWorld from '@/components/HelloWorld.vue'

export default {
  data(){
    return{
      name: localStorage.getItem('name')
    }
  },
  mounted(){
    if(!localStorage.getItem('token')){
      this.$router.push("/login");
    }
  }
}
</script>
