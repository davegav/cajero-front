<template>
    <div id="User">
        <h2>Hola <span> {{username}}, </span> ¡Bienvenido!</h2>
        <div>
        <form >
          <div>
            <label for="username">Ingrese su usuario</label>
            <input name="username" id="username">
          </div>
          <div>
            <label for="password">Ingrese su contraseña</label>
            <input name="password" id="password" value="*">
          </div>
          <div>
            <button  v-on:click="checkUser" >Autenticar</button>
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
        username: "none",
        salida: "Esperando autenticacion"
      }
    },
    methods: {
      async checkUser(){
        var element = document.getElementById("salida");
        this.salida = "Procesando!!!";
        var username = document.getElementById("username").value;
        var password = document.getElementById("password").value;
        const {data:response} = await axios.post("https://cajero-api123456.herokuapp.com/user/auth/", {"username": username, "password": password})
          .then(response => response.json())
          .then((data) => {
            this.salida = data;
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
