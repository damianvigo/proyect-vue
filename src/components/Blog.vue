<template>
  <div class="general">
    <Slider texto="Blog"></Slider>
    <!-- prop texto -->
    <div class="center">
      <section id="content">
        <h1 class="subheader">Blog</h1>

        <div id="articles" v-if="articles">
          <Articles :articles="articles"></Articles>
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
  name: "Blog",
  components: {
    Slider,
    Sidebar,
    Articles
  },
  mounted() {
    this.getArticles();
  },
  data() {
    return {
      url: Global.url,
      articles: null
    };
  },
  methods: {
    getArticles() {
      axios.get(this.url+"articles").then(res => {
        if (res.data.status == "success") {
          this.articles = res.data.articles;
          console.log(this.articles);
        }
      });
    }
  }
};
</script>