<template>
  <div id="app">
      <ol>
        <li v-for="i in datos">
          {{i._id}}-- {{i.correo}}-- {{i.password}}
        </li>
      </ol>

      <button @click="buscar">Buscar Artistas</button>


      <ul>
        <li v-for="i in artistas">
         {{i.nombre}} -- {{i.apellido}} -- {{i.musica}} <button @click="eliminar(i.id)"></button>
        </li>
      </ul>
  </div>
</template>

<script>

import axios from 'axios'
export default {
  name: 'app',
  data:()=>({
datos:null,
artistas:null,
  }),
  created() {
        axios.get('http://localhost:3000/users')
  .then(function(response){
    console.log(response.data);
    vm.datos =response.data
 
  });  
  },
  methods: {
    buscar(){
       axios.get('http://localhost:3000/artist')
  .then(function(response){
    console.log(response.data);
    vm.artistas=response.data
 
  });  
    },
    eliminar(dato){
   axios.delete('http://localhost:3000/artist', dato)
  .then(function(response){
    console.log(response.data);
  
 
  });  
    }
  },

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
