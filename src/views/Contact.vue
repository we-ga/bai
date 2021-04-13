<template>

  <div id="container">

          <h1>Student Info</h1>
        <table id="table">
         
  <thead>
    <tr>
      <th scope="col" style="font-size: 20px">Name</th>
      <th scope="col">Gender</th>
      <th scope="col">Mail</th>

    </tr>
  </thead>
  <tbody>
    <tr v-bind:key="user.id" v-for="user in users">
     <button @click="back" style="margin:10px;font-weight: bold;"> <td>{{user.full_name}}</td></button>
      <td>{{user.gender}}</td>
      <td>{{user.email_adress}}</td>
    </tr>
    
  </tbody>
</table>

  </div>
</template>

<script>
import axios from "axios";


export default {
  
  methods: {
    back() {
      this.$router.push({ name: 'Home' });
    }
  },

  data (){
  return{
    users : []
  }
},
 created: function(){
   axios.get('https://my.api.mockaroo.com/users.json?key=c06e00d0')
   .then(res => {
     this.users = res.data;
   })
 }
 
};
</script>
<style>


#app{
   font-family: 'Courier New', Courier, monospace;
 
  font-size: 20px;
   -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

}

#table {
 margin-left: 600px;
}



</style>


