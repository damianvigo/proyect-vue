<template>
  <div class="general">
    <Slider :texto="'Busqueda: ' + searchString"></Slider>
    <!-- prop texto -->
    <div class="center">
      <section id="content">
        <h1 class="subheader" v-if="articles">Artículos encontrados</h1>
        <h2 class="subheader" v-else>Sin resultados</h2>

        <div id="articles" v-if="articles">
          <Articles :articles="articles"></Articles>
        </div>

        <div v-else>
          <h2>No hay articulos que coincidan con tu busqueda</h2>
        </div>  

      </section>
      <Sidebar></Sidebar>
      <div class="clearfix"></div>
    </div>
  </div>
</template>

<script>
import Slider from "./Slider.vue";
import Sidebar from "./Sidebar.vue";
import axios from "axios";
import Global from '../Global';
import Articles from './Articles';

export default {
  name: "Search",
  components: {
    Slider,
    Sidebar,
    Articles
  },
  mounted() {
    this.searchString = this.$route.params.searchString;
    this.getArticlesBySearch(this.searchString);
  },
  data() {
    return {
      url: Global.url,
      articles: null,
      searchString: null
    };
  },
  methods: {
    getArticlesBySearch(searchString) {
      axios.get(this.url+"search/" + searchString).then(res => {
        if (res.data.status == "success") {
          this.articles = res.data.articles;
          console.log(this.articles);
        }
      });
    }
  }
};
</script>