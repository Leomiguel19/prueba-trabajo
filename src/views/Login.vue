<template>
  <div class="login-clean">
    <form
      style="background-color: rgba(255, 255, 255, 0.9)"
      @submit.prevent="login"
    >
      

      <h2 class="text-center mb-4">Iniciar Sesión</h2>
        <b-form-group>
          <b-form-input
            v-model.trim="$v.email.$model"
            type="email"
            :state="$v.email.$dirty ? !$v.email.$invalid : null"
            name="email"
            id="email"
            placeholder="Correo Electrónico"
            @blur="$v.email.$touch()"
            @input="$v.email.$reset()"
          />
          <b-form-invalid-feedback>
            Debe ingresar un correo valido
          </b-form-invalid-feedback>
        </b-form-group>
        <b-form-group class="position-relative">
          <b-form-input
            v-model.trim="$v.password.$model"
            id="input-password"
            :type="showPassword ? 'text' : 'password'"
            :state="$v.password.$dirty ? !$v.password.$invalid : null"
            name="password"
            placeholder="Password"
            @blur="$v.password.$touch()"
            @input="$v.password.$reset()"
          />
          <b-form-invalid-feedback>
            La clave debe ser minimo de 6 caracteres
          </b-form-invalid-feedback>
      </b-form-group>  
      <b-form-group>
        <b-overlay :show="overlay">
          <button
            class="btn btn-block m-auto"
            :disabled="$v.$invalid"
            type="submit"
          >
            Ingresar
          </button>
        </b-overlay>
        <span class="error">{{ error }}</span>
      </b-form-group>
      <router-link to="/login" class="forgot">Olvido su contraseña?</router-link> 
    </form>
  </div>
</template>

<script>
import { validationMixin } from 'vuelidate'
import { required, email, minLength } from 'vuelidate/lib/validators'

export default {
  mixins: [validationMixin],
    head() {
      return {
        title: 'Inicio de Sesión | Prueba-Trabajo',
        meta: [
          { content: 'Inicio de sesión | Prueba-Trabajo', property: 'og:title' },
        ],
      }
  },
  data() {
    return {
      email: '',
      password: '',
      error: '',
      showPassword: false,
      error: '',
      overlay: false,

    }
  },
  validations: {
    email: {
      required,
      email,
    },
    password: {
      required,
      minLength: minLength(6),
    },
  },
  methods: {
    login() {
    }
    }
}
</script>

<style lang="scss">
  .login-clean{
    padding-top: 100px;
    padding-bottom: 150px;
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    form {
      max-width: 420px;
      width: 90%;
      margin: 0 auto;
      background-color: #ffffff;
      padding: 40px;
      color: #505e6c;
      box-shadow: 1px 1px 5px rgba(0,0,0,0.1);
      .form-control {
        background: rgb(218, 218, 218);
        border: none;
        border-bottom: 1px solid #dfe7f1;
        border-radius: 25px;
        box-shadow: none;
        outline: none;
        color: rgb(111, 110, 110);
        text-indent: 8px;
        height: 42px;
      }
      h2{
        font-size: 24px;
        line-height: 1.5;
      }
      .btn{
        text-align: center;
        width: 50%;
        font-size: 1.2rem;
        background: rgb(29,54,95);
        //background: $color3;
        color: #dfe7f1;
        border: none;
        border-radius: 25px;
        box-shadow: none;
        margin-top: 26px;
        text-shadow: none;
        outline: none !important;
      }
      .btn, .btn-primary:hover, .btn-primary:active {
        background: rgb(29,54,95);
        //color: $color3;

      }   
      .btn-primary:active {
        transform: translateY(1px);
      }
      .forgot {
        display: block;
        text-align: center;
        font-size: 1rem;
        color: rgb(29,54,95);
        //color: $color3;
        text-decoration: none;
        &:hover, &:active {
          text-decoration: none;
        }
      }     
    }  
  } 
</style>
