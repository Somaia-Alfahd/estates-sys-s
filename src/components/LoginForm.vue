<template>
  <form @click.prevent>
    <div class="row g-3 align-items-center">
      <h1>logIn</h1>
      <div class="col-auto d-block mx-auto">
        <input
          type="text"
          class="form-control"
          placeholder="Enter your Email"
          v-model="state.email"
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
          v-model="state.pass"
        />
        <span class="error-feedback" v-if="v$.pass.$error">{{
          v$.pass.$errors[0].$message
        }}</span>
      </div>
    </div>
    <br />
    <div class="row g-3 align-items-center">
      <div class="col-auto d-block mx-auto">
        <button type="submit" @click="loginUse()" class="btn btn-primary">
          Login
        </button>
        &nbsp;&nbsp;&nbsp;&nbsp;
        <button
          type="button"
          @click="redirectTo({ val: 'SignUp' })"
          class="btn btn-secondary"
        >
          Sign Up
        </button>
        &nbsp;&nbsp;&nbsp;&nbsp;
      </div>
    </div>
  </form>
</template>
<script>
import { mapActions } from "vuex";
import useVuelidate from "@vuelidate/core";
import { required, email } from "@vuelidate/validators";
import { reactive, computed } from "vue";
export default {
  name: "LoginForm",
  setup() {
    const state = reactive({
      pass: "",
      email: "",
    });
    const rules = computed(() => {
      return {
        email: { required, email },
        pass: { required },
      };
    });
    const v$ = useVuelidate(rules, state);
    return {
      state,
      v$,
    };
  },
  data() {
    return {};
  },
  methods: {
    // signUpPage() {
    //   this.$router.push({ name: "SignUp" });
    // },
    ...mapActions(["redirectTo"]),
    loginUse() {
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
