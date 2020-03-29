<template>
    <div>
      <div class="container">
        <h2>Create user</h2>
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
            <button type="submit" class="btn btn-primary" v-on:click="addUser()">Create</button>
          </div>
        </form>
      </div>
    </div>
</template>

<script>
    export default {
      data(){
        return{
          name:'',
          city:''
        }
      },
      methods:{
        addUser(){
          axios.post('/api/users',{
            name:this.name,
            city:this.city
          });
        }
      }
    }
</script>
