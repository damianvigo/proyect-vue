<template>
  <div class="general">
    <Slider texto="Página de pruebas"></Slider>
    <div class="center">
      <section id="content">
        <h2 class="subheader">Página de pruebas</h2>
        <h3>{{id_desde_url}}</h3>
        <button @click="actualizarNombre()">Actualizar Nombre</button>
        <button @click="redirigirAlBlog()">Redirigir</button>
        <h4>{{nombre}}</h4>
        <!-- mostrar los datos de la propiedad nombre -->
      </section>
      <Sidebar></Sidebar>
      <div class="clearfix"></div>
    </div>
  </div>
</template>

<script>
import Slider from "./Slider.vue";
import Sidebar from "./Sidebar.vue";
export default {
  name: "Pagina",
    components: {
    Slider,
    Sidebar
  },
  
  created() {
    console.log("Componente creado"); // metodo del ciclo vida o HOOKS. se crea pero se ha terminado de cargar todo correctamente
  },

  mounted() {
    // metodo del ciclo de vida, se ejecuta nada mas cargar el componente. Usarlo antes que el created la mayoria de casos.
    this.id_desde_url = this.$route.params.id;
    console.log("Componente montado");
  },

  updated() {
    console.log("Componente actualizado"); // metodo del ciclo vida. Se ejecuta cada vez que el componente se actualiza
  },

  destroyed() {
    //  metodo del ciclo vida. Se ejecuta cuando el componente se elimina
    console.log("Compononente eliminado");
  },

  data() {
    // defino las propiedades que quiero. Propiedades de datos del componente
    return {
      id_desde_url: null,
      nombre: "Damian Vigo"
    };
  },

  methods: {
    // para metodos personalizados usar methods. Pone un json y a continuación los metodos que quiero.
    actualizarNombre() {
      this.nombre = "DAMIAN VIGO WEB";
      console.log(this.nombre);
    },
    redirigirAlBlog() {
      this.$router.push("/blog");
    }
  }
};
</script>