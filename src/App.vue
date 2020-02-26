<template>
  <div id="app">
    <h3>Please fetch my Github profile data</h3>
    <div v-if="error">{{error}}</div>
    <div v-else>
      <Suspense>
        <template #default>
          <Home></Home>
        </template>
        <template #fallback>
          <p>Loading...</p>
        </template>
      </Suspense>
    </div>
  </div>
</template>

<script>
import { onErrorCaptured, ref } from "vue";
import Home from "./components/Home.vue";

export default {
  name: "App",
  setup() {
    const error = ref(null);
    onErrorCaptured(e => {
      error.value = e;
      return true;
    });
    return { onErrorCaptured };
  },
  components: {
    Home
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
