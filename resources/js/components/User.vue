<template>
    <div>
      <div class="container">
        <h2 class="text-center">แสดงข้อมูล</h2>
        <table class="table table-bordered">
          <tr>
            <th>รหัส</th>
            <th>ชื่อ</th>
            <th>จังหวัด</th>
            <th>แก้ไข</th>
            <th>ลบ</th>
          </tr>
          <tr v-bind:key="user.id" v-for="(user,index) in users">
            <td>{{ user.id }}</td>
            <td>{{ user.name }}</td>
            <td>{{ user.city }}</td>
            <td><a :href="'/users/'+user.id+'/edit'" class="btn btn-primary">Edit</a></td>
            <td><a href="javascript:;" class="btn btn-danger" v-on:click="deleteUser(user.id, index)">Delete</a></td>
          </tr>
        </table>
        <a href="/users/create" class="btn btn-primary">เพิ่มข้อมูล</a>
      </div>
    </div>
</template>

<script>
    export default {
      mounted(){
        this.getUsers();
      },
      methods:{
        getUsers(){
          axios.get('/api/users').then(response => {
            this.users = response.data;
          });
        },
        deleteUser(id, index){
          axios.delete('/api/users/'+id).then(response => {
            this.users.splice(index, 1);
          });
        }
      },
      data(){
        return {
          users:[]
        }
      }
    }
</script>
