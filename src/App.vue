<template>
  <div id="app">
    <v-app>

      <!-- Sizes your content based upon application components -->
      <v-main>

        <!-- Provides the application the proper gutter -->

        <!-- If using vue-router -->
        <router-view :controller="controller"></router-view>
      </v-main>


    </v-app>
  </div>
</template>

<script>

import {SolutionManagerController} from "solution_manager_controller"

export default {
  name: "App",
  components: {},
  data() {
    return {
      controller: null
    }
  },
  mounted() {
    function httpGet(theUrl) {
      var xmlHttp = new XMLHttpRequest();
      xmlHttp.open("GET", theUrl, false); // false for synchronous request
      xmlHttp.send(null);
      return xmlHttp.responseText;
    }
    /*try {
      config = JSON.parse(httpGet("env"));
    } catch (e) {
      config = {API_URL: "http://127.0.0.1", API_PORT:30002};
    }*/
    //this.controller = new SolutionManagerController(window.location.host + "/api");
    this.controller = new SolutionManagerController("http://127.0.0.1:25000/solution_manager");
  }
}
</script>


<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
