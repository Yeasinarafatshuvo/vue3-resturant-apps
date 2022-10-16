<template>
  <Header />
  <h1>Hello, user welcome Add Resturant page</h1>
  <form class="add" @submit.prevent>
    <input
      type="text"
      name="name"
      placeholder="Enter name"
      v-model="resturant.name"
    />
    <input
      type="text"
      name="address"
      placeholder="Enter address"
      v-model="resturant.address"
    />
    <input
      type="text"
      name="contact"
      placeholder="Enter contact"
      v-model="resturant.contact"
    />
    <button @click="add_resturant">Add resturant</button>
  </form>
</template>

<script>
import axios from "axios";
import Header from "../components/Header.vue";
export default {
  name: "Add",
  components: {
    Header,
  },
  data() {
    return {
      resturant: {
        name: "",
        address: "",
        contact: "",
      },
    };
  },
  methods: {
    async add_resturant() {
      const result = await axios.post("http://localhost:3000/resturant", {
        name: this.resturant.name,
        address: this.resturant.address,
        contact: this.resturant.contact,
      });
      if (result.status == 201) {
        this.$router.push({ name: "Home" });
      }
    },
  },

  mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "Login" });
    }
  },
};
</script>

<style></style>
