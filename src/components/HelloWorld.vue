<template>
   <table class="table table-striped table-hover table-bordered border-3">
                
                <thead>
                    <tr class = "bg-dark text-white">
                        <th>#</th>
                        <th>Username</th>
                      
                    </tr>
                </thead>
                <tbody>
                     <tr v-for="user in users" :key="user.id">
                <th scope="col">{{user.id}}</th>
                <th scope="col">{{user.name}}</th>
                    </tr>
                </tbody>
             </table>
</template>
<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data()
  {
    return {
       users : []
    };
  },
  methods :
  {
    retrieveUsers()
    {
      axios.get("http://localhost:8080/api/user").then(response => {
          this.users = response.data;
      }).catch(e => {
                console.log(e);
            });
    }
  },
  mounted()
  {
     this.retrieveUsers();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
