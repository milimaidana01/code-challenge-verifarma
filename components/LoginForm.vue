<template>
  <div class="login-form-container">
    <img class="login-form-logo" src="https://i.ibb.co/QF9NmXb/daf1cd39-5d9c-4660-b505-8b6bc63fe776.jpg" />
    <div class="form">
      <div class="title">Welcome</div>
      <div class="subtitle">Login with your email:</div>
      <div class="input-container ic1">
        <input id="email" class="input" type="text" placeholder=" " />
        <div class="cut cut-short"></div>
        <label for="email" class="placeholder">Email</label>
      </div>
      <div class="input-container ic1">
        <input id="password" class="input" type="password" placeholder=" " />
        <div class="cut cut-short"></div>
        <label for="password" class="placeholder">Password</label>
      </div>
      <button type="submit" class="submit" @click="login">Login</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: "LoginForm",
  data() {
    return {
      loggedIn: false
    };
  },
  methods: {
    async login() {
      try {
        const response = await axios.get("https://www.google.com");
        console.log(response);
        this.$router.push("/HomePage");
      }
      catch (error) {
        this.$router.push("/HomePage");
      }
    }
  },
}
</script>
