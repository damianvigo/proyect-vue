<template>
  <div class="general">
    <div class="center">
      <section id="content">
        <h2 class="subheader">Peliculas</h2>

        <div class="mis-datos" v-if="misDatos">
          <!-- si existen mis datos, mostrarlos. -->
          <p v-html="misDatos"></p>
          <br />
          {{web | mayusculas | concatenaYear('Este es el mejor año')}}
          <!-- filtro -->
        </div>

        <div class="favorita" v-if="favorita">
          <h2>La pelicula Marcada es:</h2>
          <h2>{{favorita.title}}</h2>
        </div>

        <!-- Listado articulos -->
        <div id="articles">
          <!--  -->
          <div v-for="pelicula in peliculas" v-bind:key="pelicula.title">
            <Pelicula :pelicula="pelicula" @favorita="haLlegadoLaPeliculaFavorita"></Pelicula>
            <!-- variable pelicula que recorre el for se pasa a la prop y se recibie en Pelicula.vue. Con v-bind se sacan los objetos, sin los : seria un string -->
          </div>
        </div>
      </section>

      <Sidebar></Sidebar>
      <div class="clearfix"></div>
    </div>
  </div>
</template>

<script>
import Sidebar from "./Sidebar.vue";
import Pelicula from "./Pelicula.vue";

export default {
  name: "Peliculas",

  components: {
    Pelicula,
    Sidebar
  },
  methods: {
    haLlegadoLaPeliculaFavorita(favorita) {
      this.favorita = favorita;
    }
  },
  filters: {
    mayusculas(value) {
      return value.toUpperCase();
    },
    concatenaYear(value, message) {
      let date = new Date();
      return value + " " + date.getFullYear() + " " + message;
    }
  },
  computed: {
    peliculasMayuscula() {
      let peliculasMod = this.peliculas;
      for (let i = 0; i < this.peliculas.length; i++) {
        peliculasMod[i].title = peliculasMod[i].title.toUpperCase();
      }
      return peliculasMod;
    },
    misDatos() {
      return (
        this.nombre +
        " " +
        this.apellido +
        "<br/>" +
        "<strong>Sitio web:</strong> " +
        this.web
      );
    }
  },
  data() {
    return {
      nombre: "Damian",
      apellido: "Vigo",
      web: "https://damianvigo.com",
      favorita: null,

      peliculas: [
        {
          title: "Gladiador",
          year: 2000,
          image:
            "https://i2.wp.com/frasesdelapelicula.com/wp-content/uploads/2013/09/gladiador.jpg?fit=1200%2C630&ssl=1"
        },
        {
          title: 1917,
          year: 2020,
          image:
            "https://es.web.img3.acsta.net/pictures/20/01/09/15/10/0234685.jpg"
        },
        {
          title: "El conjuro 3",
          year: 2020,
          image:
            "https://depor.com/resizer/mU8zRNtZpwLbvYs9RtexiC5aRpM=/980x528/smart/arc-anglerfish-arc2-prod-elcomercio.s3.amazonaws.com/public/ATRBQGCVTRHQJAYCHJASMKTZK4.jpg"
        }
      ]
    };
  }
};
</script>