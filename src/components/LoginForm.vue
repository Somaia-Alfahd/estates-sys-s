<template>
  <form @click.prevent>
    <div class="row g-3 align-items-center">
      <h1>logIn</h1>
      <div class="col-auto d-block mx-auto">
        <input
          type="text"
          class="form-control"
          placeholder="Enter your Email"
          v-model="email"
        />
      </div>
    </div>
    <br />
    <div class="row g-3 align-items-center">
      <div class="col-auto d-block mx-auto">
        <input
          type="password"
          class="form-control"
          placeholder="Enter your password"
          v-model="pass"
        />
      </div>
    </div>
    <br />
    <div class="row g-3 align-items-center">
      <div class="col-auto d-block mx-auto">
        <button type="submit" class="btn btn-primary">Login</button>
        &nbsp;&nbsp;&nbsp;&nbsp;
        <button type="button" @click="signUpPage()" class="btn btn-primary">
          Sign Up
        </button>
        &nbsp;&nbsp;&nbsp;&nbsp;
      </div>
    </div>
  </form>
</template>
<script>
export default {
  name: "LoginForm",
  data() {
    return {
      pass: "",
      email: "",
    };
  },
  methods: {
    signUpPage() {
      this.$router.push({ name: "SignUp" });
    },
  },
};
</script>
