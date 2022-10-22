<template>
  <form @click.prevent>
    <div class="row g-3 align-items-center">
      <h1>Sign Up</h1>
      <div class="col-auto d-block mx-auto">
        <input
          type="text"
          class="form-control"
          placeholder="Enter your Name"
          v-model="name"
        />
        <span class="error-feedback" v-if="v$.name.$error">{{
          v$.name.$errors[0].$message
        }}</span>
      </div>
    </div>
    <br />
    <div class="row g-3 align-items-center">
      <div class="col-auto d-block mx-auto">
        <input
          type="text"
          class="form-control"
          placeholder="Enter your Email"
          v-model="email"
        />
        <span class="error-feedback" v-if="v$.email.$error">{{
          v$.email.$errors[0].$message
        }}</span>
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
        <span class="error-feedback" v-if="v$.pass.$error">{{
          v$.pass.$errors[0].$message
        }}</span>
      </div>
    </div>
    <br />
    <div class="row g-3 align-items-center">
      <div class="col-auto d-block mx-auto">
        <button type="submit" @click="signUpNow()" class="btn btn-primary">
          Sign
        </button>
        &nbsp;&nbsp;&nbsp;&nbsp;
        <button
          type="submit"
          @click="redirectTo({ val: 'LoginView' })"
          class="btn btn-secondary"
        >
          Login
        </button>
        &nbsp;&nbsp;&nbsp;&nbsp;
      </div>
    </div>
  </form>
</template>
<script>
import { mapActions } from "vuex";
import useVuelidate from "@vuelidate/core";
import { required, email, minLength } from "@vuelidate/validators";
export default {
  name: "HelloWorld",
  data() {
    return {
      v$: useVuelidate(),
      name: "",
      pass: "",
      email: "",
    };
  },
  validations() {
    return {
      name: { required, minlength: minLength(4) },
      email: { required, email },
      pass: { required, minlength: minLength(10) },
    };
  },
  methods: {
    ...mapActions(["redirectTo"]),
    signUpPage() {
      this.$router.push({ name: "LoginView" });
    },
    signUpNow() {
      console.log("Sign Up Now ...");
      this.v$.$validate();
      if (!this.v$.$error) {
        console.log("form Validated Successfully");
      } else {
        console.log("form Validated failed");
      }
    },
  },
};
</script>
<style lang="scss" scoped>
.error-feedback {
  color: red;
  font-size: 0.85em;
}
</style>
