<template src="./CreateArticle.html"></template>

<script>
import Sidebar from "./Sidebar.vue";
import axios from "axios";
import Global from "../Global";
import Article from "../models/Article";
import { required } from "vuelidate/lib/validators";
import swal from 'sweetalert';

export default {
  name: "CreateArticle",
  components: {
    Sidebar
  },
  data() {
    return {
      url: Global.url,
      file: "",
      article: new Article("", "", null, ""),
      submitted: false
    };
  },
  validations: {
    article: {
      title: {
        required
      },
      content: {
        required
      }
    }
  },
  mounted() {},
  methods: {
    fileChange() {
      /* recibir los datos del formulario */
      this.file = this.$refs.file.files[0]; /* con refs sacando el file que esta vinculado al campo del formulario */
    },
    save() {
      this.submitted = true;

      this.$v.$touch();
      if (this.$v.$invalid) {
        return false;
      } else {
        
        axios.post(this.url + "save", this.article).then(response => {
          
          if (response.data.status == "success") {
           
           /*Se guarda la imagen si se ha guardado bien el articulo. Adjuntar el fichero recogido con formdata.  */
            if(this.file != null && this.file != undefined && this.file != '') {
              
              const formData = new FormData();
              formData.append("file0", this.file, this.file.name);
              var articleId = response.data.article._id;
  
               axios.post(this.url + "upload-image/" + articleId, formData)
                .then(response => {
                  if (response.data.article) {

                    swal(
                      'Articulo creado',
                      'El articulo se ha creado correctamente :D',
                      'success'
                    );

                    this.article = response.data.article;
                    this.$router.push("/blog");
                  } else {
                    // Mostrar alerta de error
                    swal(
                      'Creación fallida',
                      'El articulo no se ha guardado bien :(',
                      'error'
                    );
                  }
                })
                .catch(error => {
                  console.log(error);
                });
           } else { /* Si no se envía un archivo, redirección */

              swal(
                  'Articulo creado',
                  'El articulo se ha creado correctamente :D',
                  'success'
                );

              this.article = response.data.article;
              this.$router.push("/blog");
            } 
          }
        })
      }
    }
  }
};
</script>