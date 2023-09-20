<template>
  <form @submit.prevent="submit">
    <h1 class="h3 mb-3 fw-normal text-center">Please sign in</h1>
    <div class="mb-3 d-flex justify-content-center">
      <input
        v-model="email"
        type="text"
        class="form-control w-25 row"
        placeholder="Email"
        required
      />
    </div>

    <div class="mb-3 d-flex justify-content-center">
      <input
        v-model="password"
        type="password"
        class="form-control w-25"
        placeholder="Password"
        required
      />
    </div>
    <div class="mb-3 d-flex justify-content-center">
      <button class="w-10 btn btn-lg btn-primary" type="submit">Sign in</button>
    </div>
  </form>
</template>
<script>
export default {
  name: 'login',
  data() {
    return {
      email: '',
      password: '',
    }
  },

  methods: {
    async submit() {
      let result = await fetch('https://dummyjson.com/auth/login', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        // credentials: 'include',
        body: JSON.stringify({
          username: this.email,
          password: this.password,
        }),
      }).then((res) => res.json())
      localStorage.setItem('userinfo', JSON.stringify(result.token))
      console.log(result)
      await this.$router.push('/')
    },
  },
}
</script>
<style>
.btn-group {
  margin-left: 21.5rem;
}
</style>
