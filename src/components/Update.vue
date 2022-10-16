<template>
  <Header />
  <h1>Hello, user welcome Update Resturant page</h1>
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
    <button @click="update_resturant">Update resturant</button>
  </form>
</template>

<script>
import axios from "axios";
import Header from "../components/Header.vue";
export default {
  name: "Update",
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
    async update_resturant() {
      const result = await axios.put(
        "http://localhost:3000/resturant/" + this.$route.params.id,
        {
          name: this.resturant.name,
          address: this.resturant.address,
          contact: this.resturant.contact,
        }
      );
      if (result.status == 200) {
        this.$router.push({ name: "Home" });
      }
    },
  },

  async mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "Login" });
    }
    const result = await axios.get(
      "http://localhost:3000/resturant/" + this.$route.params.id
    );
    this.resturant = result.data;
  },
};
</script>

<style></style>
