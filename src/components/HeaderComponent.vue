<template>
  <header id="header">
    <div class="center">
      <!-- LOGO -->
      <div id="logo">
        <img src="../assets/logo.png" class="app-logo" alt="logo" />
        <span id="brand">
          <strong>Vue</strong>
        </span>
      </div>
      <!-- MENU -->
      <nav id="menu">
        <ul>
          <li>
            <router-link to="/home" active-class="active">Inicio</router-link>
          </li>
          <li>
            <router-link to="/blog" active-class="active">Blog</router-link>
          </li>
          <li>
            <router-link to="/formulario" active-class="active">Formulario</router-link>
          </li>
          <li>
            <router-link to="/peliculas" active-class="active">Peliculas</router-link>
          </li>
          <li>
            <router-link
              :to="{name: 'pagina', params: {id: 'Soy el valor del parametro'}}"
              active-class="active"
            >Página</router-link>
            <!-- Pasando un objeto. Directiva de atributo // :to="" -->
          </li>
        </ul>
      </nav>
      <div class="clearfix"></div>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderComponent"
};
</script>