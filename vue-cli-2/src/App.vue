<template>
  <div id="app">
    <SigninForm />
    <router-view/>
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
<script>
import Vue from "vue";
import {Component} from "vue-property-decorator";
import SigninForm from "@/components/SigninForm";

@Component({
  components: {SigninForm}
})
export default class App extends Vue {
}
</script>