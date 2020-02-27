<template>
  <div>
    <h3>Welcome to our Vue suspense demo in action</h3>
    <div>
      <h3>I am {{userInfo.name}}</h3>
      <span>
        <u>Find me on</u>
      </span>
      <p>Github: {{userInfo.github}}</p>
      <p>Twitter: {{userInfo.twitter}}</p>
      <p>Dribbble: {{userInfo.dribbble}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  async setup() {
    const userInfo = await fetchUser();
    return { userInfo };
  }
};

function timeout(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function fetchUser() {
  await timeout(4000);
  return {
    name: "Ishan Manandhar",
    github: "https://github.com/ishan-me",
    twitter: "https://twitter.com/ishan02016",
    dribbble: "https://dribbble.com/ishan-manandhar"
  };
}
</script>

<style scoped>
h3 {
  margin-top: 70px;
}
</style>
