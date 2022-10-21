<template>
  <form @click.prevent>
    <div class="row g-3 align-items-center">
      <h1>Sign Up</h1>
      <div class="col-auto d-block mx-auto">
        <input type="text" class="form-control" placeholder="Enter your Name" />
      </div>
    </div>
    <br />
    <div class="row g-3 align-items-center">
      <div class="col-auto d-block mx-auto">
        <input
          type="text"
          class="form-control"
          placeholder="Enter your Email"
        />
      </div>
    </div>
    <br />
    <div class="row g-3 align-items-center">
      <div class="col-auto d-block mx-auto">
        <input
          type="text"
          class="form-control"
          placeholder="Enter your Number"
        />
      </div>
    </div>
    <br />
    <div class="row g-3 align-items-center">
      <div class="col-auto d-block mx-auto">
        <button type="submit" class="btn btn-secondary">Sign</button>
      </div>
    </div>
  </form>
</template>
<script>
export default {
  name: "HelloWorld",
};
</script>
