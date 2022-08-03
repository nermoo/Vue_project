<template>
  <div id="app">
    <div v-if="loading">
      <Loader />
    </div>
    <CardComp  :usersList="users" />
  </div>
</template>

<script>

import CardComp from './components/CardComp.vue'
import axios from 'axios'
import Loader from './components/loadingScreen.vue'
// import {getUsers,createUser} from './services/UserServices';

export default {
  name: 'App',
  components: {
    CardComp,
    Loader
},

data:()=>({
  loading:false,
    users:[] 
}),

async created(){
  this.loading=true;
    try{
      const userData=await axios.get('https://jsonplaceholder.typicode.com/users');
      this.users=userData.data;
      console.log(this.users);
      this.loading=false;

    }catch(e){
      console.log(e);
    }
}
,
methods:{

  // getUsers(){
  //   getUsers().then(response=>{
  //     console.log(response);
  //     this.users=response;
  //   })
  // },

  // createUser(){
  //   createUser().then(response=>{
  //     console.log(response);
  //   })
  // }

}


}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
