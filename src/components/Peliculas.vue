<template>
  <section id="content">
    <h2 class="subheader">Peliculas</h2>

    <!-- Listado articulos -->
    <div id="articles">
      <article class="article-item" v-for="pelicula in peliculas" v-bind:key="pelicula.title">
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
        <div class="clearfix"></div>
      </article>
    
    
    </div>
  </section>
</template>

<script>
export default {
  
  name: 'Peliculas',

  data() {
    return {
      peliculas: [
        {title: 'Gladiador', year: 2000, image:'https://i2.wp.com/frasesdelapelicula.com/wp-content/uploads/2013/09/gladiador.jpg?fit=1200%2C630&ssl=1'},
        {title: 1917, year: 2020, image: 'https://es.web.img3.acsta.net/pictures/20/01/09/15/10/0234685.jpg'},
        {title: 'El conjuro 3', year: 2020, image: 'https://depor.com/resizer/mU8zRNtZpwLbvYs9RtexiC5aRpM=/980x528/smart/arc-anglerfish-arc2-prod-elcomercio.s3.amazonaws.com/public/ATRBQGCVTRHQJAYCHJASMKTZK4.jpg' }
      ]
    }
  }
};
</script>