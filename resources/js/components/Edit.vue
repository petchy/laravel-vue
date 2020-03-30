<template>
    <div>
      <div class="container">
        <h2>Edit user</h2>
        <form action="/users">
          <div class="form-group">
            <label>ชื่อ:</label>
            <input type="text" class="form-control" v-model="name">
          </div>
          <div class="form-group">
            <label>จังหวัด:</label>
            <input type="text" class="form-control" v-model="city">
          </div>
          <div class="form-group">
            <button type="submit" class="btn btn-primary" v-on:click="updateUser()">Edit</button>
          </div>
        </form>
      </div>
    </div>
</template>

<script>
    export default {
      props:['id'],
      data(){
        return{
          name:'',
          city:''
        }
      },
      mounted(){
        axios.get('/api/users/'+this.id).then(response=>{
          var user = response.data;
          this.name = user.name;
          this.city = user.city;
        });
      },
      methods:{
        updateUser(){
          axios.put('/api/users/'+this.id, {
            name:this.name,
            city:this.city
          });
        }
      }
    }
</script>
