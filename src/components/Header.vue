<template>
  <div class="nav">
    <router-link to="/">Home</router-link>
    <router-link to="/add">Add Resturant</router-link>
    <a href="#" @click="logout">Logout</a>
  </div>
</template>

<script>
export default {
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ name: "Login" });
    },
  },
};
</script>

<style>
.nav {
  background: #333;
  overflow: hidden;
  text-align: left;
}

.nav a {
  text-decoration: none;
  color: white;
  padding: 20px 20px;
  font-size: 20px;
  text-align: left;
}
.nav a:hover {
  background: #ddd;
}
</style>
