<template>
    <section id="content">
    <h2 class="subheader">{{titulo}}</h2>
      <hr/>
      <h1>Este es MI COMPONENTE</h1>
      <h2>{{subtitulo}}</h2>
      <hr/>

    <h2>Reactividad</h2>
    <input type="text" v-model="nombre" /> <!-- directiva v-model. Funcionalidad a elementos html -->
    Mi nombre es: <strong>{{nombre}}</strong>

    <h2>Directivas condicionales</h2>
    <input type="number" v-model="edad" />
    Mi edad es: <strong>{{edad}}</strong> <!-- dobles llaves de interpolación -->

    <p class="alert-success-provisional" v-if="edad && edad >=18 && edad < 65">
      Eres mayor de edad
    </p>

    <p class="alert-purple-provisional" v-else-if="edad && edad >=65">
      Eres de avanzada edad
    </p>

     <!-- <p class="alert-danger-provisional" v-if="edad && edad < 18"> -->
    <p class="alert-danger-provisional" v-else>
      Eres menor de edad
    </p>

    <h2>Directiva iterativa</h2>
      <ol>
        <li v-for="pelicula in peliculas" :key="pelicula">{{pelicula}}</li> <!-- para evitar el warning usar la key, para que vue sepa a que elemento de html hace referencia -->
     </ol> 

    </section>
</template>

<script>
export default {
  name: 'MiComponente',
  data() { // Modelo de datos
    return {
      titulo: 'Mi Componente', // titulo: // es una propiedad
      subtitulo: 'Soy el subtitulo de mi componente', // subtitulo: // es una propiedad
      nombre: '', // vincular el campo con el input
      edad: 18,
      peliculas: ['Gladiador', 'El señor de los anillos', '1917', 'Anabelle']
    }
  }
}
</script>