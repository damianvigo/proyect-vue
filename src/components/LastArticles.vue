<template>
  <div class="general">
    <Slider texto="Bienvenido a mi blog en Vue" home="true"></Slider>
    <div class="center">
      <section id="content">
        <h2 class="subheader">Últimos artículos</h2>

        <!-- Listado articulos -->
        <div id="articles">
          <Articles v-bind:articles="articles"></Articles>
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
import Articles from "./Articles.vue";
import Global from "../Global";

export default {
  name: "LastArticles",
  components: {
    Slider,
    Sidebar,
    Articles
  },
  mounted() {
    this.getLastArticles();
  },
  data() {
    return {
      url: Global.url,
      articles: null
    };
  },
  methods: {
    getLastArticles() {
      axios.get(this.url + "articles/true").then(res => {
        if (res.data.status == "success") {
          this.articles = res.data.articles;

          console.log(this.articles);
        }
      });
    }
  }
};
</script>