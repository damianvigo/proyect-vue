<template>
  <article class="article-item">
        <div class="image-wrap">
          <img 
            :src="pelicula.image" 
            :alt="pelicula.title"
            v-bind:title="pelicula.title"
            />  <!-- bindear una propiedad de html :src ES LO MISMO QUE SOLO DOS PUNTOS-->
        </div>

        <h2>{{pelicula.title}}</h2> 
        <span class="date" v-bind:class="{ // IMPORTANTE V-BIND Y : ES LO MISMO, SE PUEDE APLICAR CONDICIONES
          yeargreen: pelicula.year >= 2020,
          yearred: pelicula.year < 2020,
        }" > 
          {{pelicula.year}}
        </span>
        <a href="#">Leer más</a>

        <input type="button" value="Marcar como favorita" 
                @click="pasarFavoritaAlPadre(pelicula)"
        />

        <div class="clearfix"></div>
      </article>
</template>

<script>
export default {
  name: 'Pelicula',
  props: ['pelicula'],
  methods: {
    pasarFavoritaAlPadre(pelicula) {
      this.$emit('favorita', pelicula);
    }
  }
}
</script>