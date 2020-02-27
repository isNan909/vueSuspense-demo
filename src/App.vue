<template>
  <div id="app">
    <h3>See Github Profile Data</h3>
    <div v-if="error">{{error}}</div>
    <div v-else>
      <Suspense>
        <template #default>
          <Home></Home>
        </template>
        <template #fallback>
          <div class="myLoader">
            <div></div>
            <div></div>
            <div></div>
            <div></div>
            <div></div>
            <div></div>
            <div></div>
            <div></div>
          </div>
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
    return { error };
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
.myLoader {
  display: inline-block;
  position: relative;
  width: 80px;
  height: 80px;
}
.myLoader div {
  animation: lmyLoader 1.2s cubic-bezier(0.5, 0, 0.5, 1) infinite;
  transform-origin: 40px 40px;
}
.myLoader div:after {
  content: " ";
  display: block;
  position: absolute;
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: #fff;
  margin: -4px 0 0 -4px;
}
.myLoader div:nth-child(1) {
  animation-delay: -0.036s;
}
.myLoader div:nth-child(1):after {
  top: 63px;
  left: 63px;
}
.myLoader div:nth-child(2) {
  animation-delay: -0.072s;
}
.myLoader div:nth-child(2):after {
  top: 68px;
  left: 56px;
}
.myLoader div:nth-child(3) {
  animation-delay: -0.108s;
}
.myLoader div:nth-child(3):after {
  top: 71px;
  left: 48px;
}
.myLoader div:nth-child(4) {
  animation-delay: -0.144s;
}
.myLoader div:nth-child(4):after {
  top: 72px;
  left: 40px;
}
.myLoader div:nth-child(5) {
  animation-delay: -0.18s;
}
.myLoader div:nth-child(5):after {
  top: 71px;
  left: 32px;
}
.myLoader div:nth-child(6) {
  animation-delay: -0.216s;
}
.myLoader div:nth-child(6):after {
  top: 68px;
  left: 24px;
}
.myLoader div:nth-child(7) {
  animation-delay: -0.252s;
}
.myLoader div:nth-child(7):after {
  top: 63px;
  left: 17px;
}
.myLoader div:nth-child(8) {
  animation-delay: -0.288s;
}
.myLoader div:nth-child(8):after {
  top: 56px;
  left: 12px;
}
@keyframes myLoader {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
