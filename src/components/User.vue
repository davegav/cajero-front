<template>
    <div id="User">
        <h2>Hola <span> {{username}}, </span> ¡Bienvenido!</h2>
        <div>
        <form v-on:submit.prevent="processAuthUser">
          <div>
            <label for="username">Ingrese su usuario</label>
            <input type="text" v-model="user_in.username" placeholder="Username">
          </div>
          <div>
            <label for="password">Ingrese su contraseña</label>
            <input type="password" v-model="user_in.password" placeholder="Password">
          </div>
          <div>
            <button type="submit">Autenticar</button>
          </div>
        </form>
        <h1 id="salida">{{salida}}</h1>
      </div>
    </div>
</template>

<script>
  import axios from 'axios';
   export default {
    name: "User",
    data:function(){
      return {
        user_in: {
          username: "",
          password: "",
        },
        salida: "Esperando autenticacion"
      }
    },
    methods: {
      processAuthUser: function(){
        var self = this
        axios.post("https://cajero-api123456.herokuapp.com/user/auth/", self.user_in,  {headers: {}})
          .then((result) => {
            this.salida = "Autorización exitosa";
          })
          .catch((error) => {
          })
      }
    },
    created: function(){
      this.username = this.$route.params.username
    }

  }
</script>

<style>
  #User{
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  #User h2{
    font-size: 50px;
    color: #283747;
  }
  #User span{
    color: crimson;
    font-weight: bold;
  }
</style>
