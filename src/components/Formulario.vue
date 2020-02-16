<template>
  <div class="general">
    <div class="center">
      <section id="content">
        <h2 class="subheader">Formulario</h2>

        <form class="mid-form" @submit.prevent="mostrarUsuario()">
          <!-- evento @submit o v-on:submit. LLama al metodo mostrarUsuario -->
          <div class="form-group">
            <label for="apellidos">Apellido</label>
            <input type="text" name="nombre" v-model="user.nombre" />
            <div v-if="submitted && !$v.user.nombre.required">Este campo es requerido</div>
            <div v-if="submitted & !$v.user.nombre.minLength">Este campo debe tener mas caracteres</div>
          </div>

          <div class="form-group">
            <label for="nombre">Nombre</label>
            <input type="text" name="nombre" v-model="user.apellido" />
            <div v-if="submitted & !$v.user.apellido.required">Este campo es requerido</div>
            <div v-if="submitted & !$v.user.apellido.minLength">Este campo debe tener mas caracteres</div>
          </div>

          <div class="form-group">
            <label for="bio">Biografía</label>
            <textarea name="bio" v-model="user.bio"></textarea>
            <div v-if="submitted & !$v.user.bio.required">Este campo es requerido</div>
            <div v-if="submitted & !$v.user.bio.minLength">Este campo debe tener mas caracteres</div>
          </div>

          <div class="form-group radibuttons">
            <input type="radio" name="genero" value="hombre" checked v-model="user.genero" />Hombre
            <input type="radio" name="genero" value="mujer" v-model="user.genero" />Mujer
            <input type="radio" name="genero" value="otro" v-model="user.genero" />Otro
          </div>

          <div class="clearfix"></div>

          <input type="submit" value="Enviar" class="btn btn-success" />
        </form>

        <div class="datos" v-if="user.nombre && user.apellido">
          <h3>{{user.nombre + ' ' + user.apellido}}</h3>
        </div>
      </section>
      <Sidebar></Sidebar>
      <div class="clearfix"></div>
    </div>
  </div>
</template>

<script>
import { required, minLength } from "vuelidate/lib/validators";
import Sidebar from "./Sidebar.vue";
export default {
  name: "Formulario",
  components: {
    Sidebar
  },
  validations: {
    user: {
      nombre: {
        required,
        minLength: minLength(2)
      },
      apellido: {
        required,
        minLength: minLength(2)
      },
      bio: {
        required,
        minLength: minLength(10)
      }
    }
  },
  data() {
    return {
      submitted: false,
      user: {
        nombre: "",
        apellido: "",
        biografia: "",
        genero: ""
      }
    };
  },
  methods: {
    mostrarUsuario() {
      console.log(this.user);
      this.submitted = true; /* para ver que el formulario se ha enviado */

      this.$v.$touch(); /* se han tocado los campos que quiero validar */
      if (this.$v.$invalid) {
        return false;
      }

      alert("Validacion pasada");
    }
  }
};
</script>