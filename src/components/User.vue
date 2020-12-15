<template>
    <div id="User">
        <h2>Hola <span> {{username}}, </span> ¡Bienvenido!</h2>
    </div>

    <div>
      <form action="https://cajero-api123456.herokuapp.com/user/auth/" method="POST">
        <div>
          <label for="username">Ingrese su usuario</label>
          <input name="username" id="username">
        </div>
        <div>
          <label for="password">Ingrese su contraseña</label>
          <input name="password" id="password" value="*">
        </div>
        <div>
          <button>Autenticar</button>
        </div>
      </form>
    </div>

</template>

<script>
  export default {
    name: "User",
    data:function(){
      return {
        username: "none"
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
