<template>
  <div>
    <p>{{ message }}</p>
    <a href="/login" class="w-100 btn btn-lg btn-primary" v-if="!auth">login</a>
    <a href="/register" class="w-100 btn btn-lg btn-primary" v-if="!auth">register</a>
    <a href="#" class="w-100 btn btn-lg btn-primary" v-if="auth" @click="logout"
      >logout</a
    >
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "IndexPage",
  data() {
    return {
      message: "",
      auth: false,
    };
  },
  async mounted() {
    try {
      this.$nuxt.$on("auth", (auth) => {
        console.log("auth", auth);
        this.auth = auth;
      });

      const response = await fetch("http://localhost:8000/api/user", {
        method: "get",
        headers: { "Content-Type": "application/json" },
        credentials: "include",
      });

      const content = await response.json();
      console.log("content", content);

      this.message = "Hi  " + content.name + ". nice to meet you";

      this.$nuxt.$emit("auth", true);
    } catch (error) {
      this.message = "You are not logged in";

      this.$nuxt.$emit("auth", false);
    }
  },
  methods: {
    async logout() {
      await fetch("http://localhost:8000/api/logout", {
        method: "post",
        headers: { "Content-Type": "application/json" },
        credentials: "include",
      });

      await this.$router.push("/login");
    },
  },
});
</script>
