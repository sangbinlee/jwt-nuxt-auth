<template>
  <main class="form-signin w-100 m-auto">
    <form @submit.prevent="submit">
      <h1 class="h3 mb-3 fw-normal">Please sign in</h1>

      <div class="form-floating">
        <input
          type="email"
          class="form-control"
          v-model="email"
          placeholder="name@example.com"
          required
        />
        <label for="email">Email address</label>
      </div>
      <div class="form-floating">
        <input
          type="password"
          class="form-control"
          v-model="password"
          placeholder="Password"
          required
        />
        <label for="password">Password</label>
      </div>

      <button class="w-100 btn btn-lg btn-primary my-3" type="submit">login</button>
      <a href="/" class="w-100 btn btn-lg btn-primary my-3" type="submit">home</a>
      <p class="mt-5 mb-3 text-muted">&copy; 2017–2022</p>
    </form>
  </main>
</template>

<script>
export default {
  name: "login",
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async submit() {
      await fetch("http://localhost:8000/api/login", {
        method: "post",
        headers: { "Content-Type": "application/json" },
        credentials: "include",
        body: JSON.stringify({
          email: this.email,
          password: this.password,
        }),
      });

      await this.$router.push("/");
    },
  },
};
</script>
