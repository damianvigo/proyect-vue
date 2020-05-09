<template>
  <h1>Rediriguiendo...</h1>
</template>

<script>
export default {
  name: "Redirect",
  mounted() {
    let searchString = this.$route.params.searchString;
    this.$router.push("/buscador/" + searchString);
  }
};
</script>

