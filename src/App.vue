<template>
  <router-view></router-view>
</template>

<script>
import SignUp from "./components/SignUp.vue";
export default {
  components: {
    SignUp,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  padding: 0;
  margin: 0;
}
img {
  height: 100px;
  widows: 100px;
}

.register input,
.login input,
.add input {
  width: 300px;
  height: 40px;
  display: block;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 30px;
  border: 1px solid skyblue;
  padding-left: 20px;
}

.register button,
.login button,
.add button {
  width: 320px;
  height: 40px;
  border: 1px solid skyblue;
  background: skyblue;
  cursor: pointer;
  color: #fff;
}
</style>
