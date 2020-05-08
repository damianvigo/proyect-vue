<template>
  <aside id="sidebar">
    <div id="nav-blog" class="sidebar-item">
      <h3>Crear Artículo</h3>
      <router-link to="/crear-articulo" class="btn btn-success">Comienza</router-link>
    </div>
    <div id="search" class="sidebar-item">
      <h3>Descubre</h3>
      <p>Encuentra tu artículo</p>
      <form @submit.prevent="goSearch">
        <input type="text" name="search" v-model="searchString" />
        <!-- vinculando la propiedad searchString con el metodo goSearch -->
        <input type="submit" name="submit" value="Buscar" class="btn" />
      </form>
    </div>
  </aside>
</template>

<script>
export default {
  name: "Sidebar",
  data() {
    return {
      searchString: null
    };
  },
  methods: {
    goSearch() {
      this.$router.push("/redirect/" + this.searchString); /* redireción */
    }
  }
};
</script>