<template>
  <div id="app">
     <Navbar />

      <div class="container">
        <div class="card card-body">
            <h1><b>Github</b><i style="color: #ccc">Search</i></h1>
            <input @keyup="getUser" type="text" placeholder="Digite um nome para encontrar usuarios e repositrios" class="form-control" required id="search">
        </div>

      <div class="row mt-2" v-if="user.length !==0">
        <div class="col-md-4">
          <Perfil :user="user" />
        </div>
        <div class="col-md-8">
          <Repo v-for="repo in repos" :key="repo" :repo="repo" />
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
import Perfil from './components/Perfil.vue';
import Repo from './components/Repositorios.vue';
import axios from 'axios'; 
export default {
  name: 'App',
  
  data(){
    return{
      github:{
        url: "https://api.github.com/users",
        cliente_id: "Iv1.0099181f53c33d07",
        cliente_secret: "181ba680e6c75448cf878427952c5f401f309161",
        count: 7,
        sort: "created: asc"
      },
      user: [],
      repos: []
    };
  },
  components: {
  Navbar,
  Perfil,
  Repo
  },

  methods: {

    getUser(e){
      const user = e.target.value;
      const { url, client_id, client_secret, sort, count} = this.github;

      axios.get(
        `${url}/${user}?client_id=${client_id}&client_secret=${client_secret}`
      ).then(({data}) => this.user = data);

      axios.get(
        `${url}/${user}/repos?per_page=${count}&sort${sort}&client_id=${client_id}&client_secret=${client_secret}`
      ).then(({data}) => this.repos = data); 
    }
  }
}
</script>

<style>
#app{
 
}
</style>


