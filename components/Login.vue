<!-- Please remove this file from your project -->
<template>
  <main class="form-signin w-100 m-auto">
    <form>
      <h1 class="h3 mb-3 fw-normal">Please sign in</h1>

      <div class="form-floating">
        <input type="text" class="form-control" v-model="name" placeholder="name" />
        <label for="name">Email address</label>
      </div>
      <div class="form-floating">
        <input
          type="email"
          class="form-control"
          v-model="email"
          placeholder="name@example.com"
        />
        <label for="email">Email address</label>
      </div>
      <div class="form-floating">
        <input
          type="password"
          class="form-control"
          v-model="Password"
          placeholder="Password"
        />
        <label for="Password">Password</label>
      </div>

      <button class="w-100 btn btn-lg btn-primary my-3" type="submit">login</button>
      <button class="w-100 btn btn-lg btn-primary" type="submit">Sign in</button>
      <p class="mt-5 mb-3 text-muted">&copy; 2017–2022</p>
    </form>
  </main>
</template>

<script>
export default {};
</script>

<style>
html,
body {
  height: 100%;
  width: 100%;
  text-align: center;
}

.form-signin {
  max-width: 330px;
  padding: 15px;
}

.form-signin .form-floating:focus-within {
  z-index: 2;
}

.form-signin input[type="email"] {
  margin-bottom: -1px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}

.form-signin input[type="password"] {
  margin-bottom: 10px;
  border-top-left-radius: 0;
  border-top-right-radius: 0;
}
</style>
