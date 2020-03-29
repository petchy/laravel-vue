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
          <tr v-for="user in users">
            <td>{{ user.id }}</td>
            <td>{{ user.name }}</td>
            <td>{{ user.city }}</td>
            <td><a href="#" class="btn btn-primary">Edit</a></td>
            <td><a href="#" class="btn btn-warning">Delete</a></td>
          </tr>
        </table>
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
          axios.get('api/users').then(response => {
            this.users = response.data;
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
