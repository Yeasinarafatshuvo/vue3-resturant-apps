<template>
  <img src="../assets/resturant_logo.png" />
  <h1>Sign Up</h1>
  <div class="register">
    <input type="text" placeholder="Enter name" v-model="name" />
    <input type="text" placeholder="Enter email" v-model="email" />
    <input type="text" placeholder="Enter password" v-model="password" />
    <button @click="signUp">Sign Up</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "SignUp",
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    async signUp() {
      let result = await axios.post("http://localhost:3000/user", {
        name: this.name,
        email: this.email,
        password: this.password,
      });

      if (result.status == 201) {
        alert("sign up successfully done");
        localStorage.setItem("user-info", JSON.stringify(result.data));
      }
      console.log(result);
    },
  },
};
</script>

<style scoped>
img {
  height: 100px;
  widows: 100px;
}

.register input {
  width: 300px;
  height: 40px;
  display: block;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 30px;
  border: 1px solid skyblue;
  padding-left: 20px;
}

.register button {
  width: 320px;
  height: 40px;
  border: 1px solid skyblue;
  background: skyblue;
  cursor: pointer;
  color: #fff;
}
</style>
