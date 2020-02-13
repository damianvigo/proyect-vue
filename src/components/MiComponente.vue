<template>
    <section id="content">
    <h2 class="subheader">{{titulo}}</h2>
      <hr/>
      <h1>Este es MI COMPONENTE</h1>
      <h2>{{subtitulo}}</h2>
      <hr/>

    <h2>Reactividad</h2>
    <input type="text" />

    </section>
</template>

<script>
export default {
  name: 'MiComponente',
  data() {
    return {
      titulo: 'Mi Componente', // titulo: // es una propiedad
      subtitulo: 'Soy el subtitulo de mi componente' // subtitulo: // es una propiedad
    }
  }
}
</script>