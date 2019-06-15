<template>
  <nav class="navbar navbar-dark bg-dark">
    <a class="navbar-brand">Tonoy</a>
    <form class="form-inline" @submit.prevent="search">
      <input
        class="form-control mr-sm-2"
        type="search"
        placeholder="Search"
        aria-label="Search"
        v-model="keyword"
      >
      <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
    </form>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      keyword: ""
    };
  },
  methods: {
    search() {
      this.$emit("search", this.keyword);
    }
  }
};
</script>

<style>
</style>
