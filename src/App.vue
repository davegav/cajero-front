<template>
  <div id="app">
    <div class="header">
      <h1>Banco UN</h1>
      <nav>
        <button v-on:click="init" v-if="is_auth" > Inicio </button>
        <button v-on:click="getBalance" v-if="is_auth" > Saldo </button>
        <button v-if="is_auth" > Transacción </button>
        <button v-if="is_auth" >Cerrar Sesión</button>
      </nav>
    </div>
    <div class="main-component">
      <h1 class="body" >La pagina de spiderman</h1>
      <img src="./assets/spidy.jpg" alt="Spidy" width="360" height="180">

      <table style="width:50%">
        <tr>
          <th>Firstname</th>
          <th>Lastname</th>
          <th>Age</th>
        </tr>
        <tr>
          <td>Jill</td>
          <td>Smith</td>
          <td>50</td>
        </tr>
        <tr>
          <td>Eve</td>
          <td>Jackson</td>
          <td>94</td>
        </tr>
      </table>

    </div>

    <div class="footer">
      <h2>Misión TIC 2022</h2>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'App',
    components: {},
    data: function(){
      return {
      is_auth: localStorage.getItem('isAuth') || false
      }
    },
    methods: {},
    beforeCreate: function(){
      localStorage.setItem('current_username', 'camilo24')
      localStorage.setItem('isAuth', true)
    }
  }
</script>

<style>
  table {
    border: 3px solid black;
    border-collapse: collapse;
  }
  th  {
    border: 2px solid black;
    border-collapse: collapse;
    padding: 10px;
  }
  td {
    border: 1px solid black;
    border-collapse: collapse;
    padding: 10px;
    text-align: center;
  }


  body{
    margin: 10 10 10 10;
  }
  .header{
    margin: 0%;
    padding: 0;
    width: 100%;
    height: 10vh;
    min-height: 100px;
    background-color: #283747 ;
    color:#E5E7E9 ;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .header h1{
    width: 20%;
    text-align: center;
  }
  .header nav {
  height: 100%;
  width: 45%;
  display: flex;
  justify-content: space-around;
  align-items: center;
  font-size: 20px;
  }
  .header nav button{
  color: #E5E7E9;
  background: #283747;
  border: 1px solid #E5E7E9;
  border-radius: 5px;
  padding: 10px 20px;
  }
  .header nav button:hover{
  color: #283747;
  background: #E5E7E9;
  border: 1px solid #E5E7E9;
  }
  .main-component{
  height: 75vh;
  margin: 0%;
  padding: 0%;
  background: #FDFEFE ;
  }
  .footer{
  margin: 0;
  padding: 0;
  width: 100%;
  height: 10vh;
  min-height: 100px;
  background-color: #283747;
  color: #E5E7E9;
  }
  .footer h2{
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
