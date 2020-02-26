<template>
  <div>
    <div>
      <button @click="fetchData">Get data</button>
      <p>{{userData}}</p>
    </div>
  </div>
</template>

<script>
import { axios } from "axios";
export default {
  name: "Home",
  async setup() {
    const user = null;
    const userData = await fetchData();
    return { ...userData, user };
  }
};
function fetchData() {
  axios
    .get("https://api.github.com/users/ishan-me")
    .then(response => (this.user = response.data))
    .catch(error => console.log(error));
}
</script>

<style scoped>
h3 {
  margin-bottom: 30px;
}
</style>