<template>
  <form @submit.prevent="submit">
    <h1 class="h3 mb-3 fw-normal">Please register</h1>

    <div class="form-floating">
      <input
        type="text"
        class="form-control"
        v-model="name"
        placeholder="name"
        required
      />
      <label for="name">Email address</label>
    </div>
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
      <label for="Password">Password</label>
    </div>

    <button class="w-100 btn btn-lg btn-primary" type="submit">register</button>
    <p class="mt-5 mb-3 text-muted">&copy; 2017–2022</p>
  </form>
</template>

<script>
export default {
  name: "register",
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    async submit() {
      await fetch("http://localhost:8000/api/register", {
        method: "post",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          name: this.name,
          email: this.email,
          password: this.password,
        }),
      });
      await this.$router.push("/login");
    },
  },
};
</script>
