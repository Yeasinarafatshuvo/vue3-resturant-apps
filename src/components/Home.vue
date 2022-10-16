<template>
  <Header />
  <h1>Hello, {{ name }} welcome to home page</h1>
  <table border="1">
    <tr>
      <td>Id</td>
      <td>Name</td>
      <td>Contact</td>
      <td>Address</td>
      <td>Action</td>
    </tr>
    <tr v-for="item in resturant" :key="item.id">
      <td>{{ item.id }}</td>
      <td>{{ item.name }}</td>
      <td>{{ item.contact }}</td>
      <td>{{ item.address }}</td>
      <td>
        <router-link :to="'/update/' + item.id">Update</router-link>
        <button @click="delete_resturant(item.id)">Delete</button>
      </td>
    </tr>
  </table>
</template>

<script>
import Header from "../components/Header.vue";
import axios from "axios";
export default {
  name: "Home",
  components: {
    Header,
  },
  data() {
    return {
      name: "",
      resturant: [],
    };
  },
  methods: {
    async delete_resturant(id) {
      let result = await axios.delete("http://localhost:3000/resturant/" + id);
      if (result.status == 200) {
        this.loadData();
      }
    },
    async loadData() {
      let user = localStorage.getItem("user-info");
      this.name = JSON.parse(user).name;
      if (!user) {
        this.$router.push({ name: "SignUp" });
      }

      let result = await axios.get("http://localhost:3000/resturant");
      this.resturant = result.data;
    },
  },

  async mounted() {
    this.loadData();
  },
};
</script>

<style>
table tr {
  padding: 10px;
}
table td {
  width: 16px;
  height: 40px;
}
</style>
