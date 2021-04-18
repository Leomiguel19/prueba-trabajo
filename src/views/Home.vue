<template>
  <div class="home">
    <div id="nav">
      <router-link to="/">| Home | </router-link>
      <a v-on:click="logout()">logout | </a>
    </div>
    <h2>Welcome to my application</h2>
    <h2>{{ name }}</h2>
  </div>
</template>

<script>
//import HelloWorld from '@/components/HelloWorld.vue'

export default {
  data() {
    return {
      name: localStorage.getItem("name"),
    };
  },
  mounted() {
    if (!localStorage.getItem("token")) {
      this.$router.push("/login");
    }
  },
  methods: {
    logout() {
      localStorage.removeItem("name");
      localStorage.removeItem("token");
      this.$router.push("/login");
    },
  },
};
</script>

<style lang="scss">
#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;
    .logout {
      cursor: pointer;
    }

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
