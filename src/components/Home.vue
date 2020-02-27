<template>
  <div>
    <div>
      <button @click="fetchData">See User</button>
      <p>{{userData}}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Home",
  async setup() {
    const userData = null;
    function fetchData() {
      axios
        .get("https://api.github.com/users/ishan-me", {
          headers: {
            Authorization: "token 3214e261fb98e85a0849054bd19deeda2344dfd7"
          }
        })
        .then(response => response.data)
        .catch(error => console.log(error));
    }
    return { ...fetchData, userData };
  }
};
</script>

<style scoped>
h3 {
  margin-bottom: 30px;
}
</style>