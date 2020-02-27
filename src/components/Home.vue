<template>
  <div>
    <div>
      <button @click="fetchData">See data</button>
      <p>{{user}}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Home",
  async setup() {
    const user = null;
    const userData = fetchData();
    return { ...userData, user };
  }
};
function fetchData() {
  axios
    .get("https://api.github.com/users/ishan-me", {
      headers: {
        Authorization: "token 3214e261fb98e85a0849054bd19deeda2344dfd7"
      }
    })
    .then(response => (this.user = response.data))
    .catch(error => console.log(error));
}
</script>

<style scoped>
h3 {
  margin-bottom: 30px;
}
</style>