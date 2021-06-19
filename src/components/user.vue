<template>
  <div>
    <div> Tugas Web </div>
    <ul>
      <li v-for="i in users" :key="i.id"> {{i.username}}
        <button @click="hapus(i.id)">X</button>
      </li>
    </ul>
      <input v-model="username"/>
      <input v-model="password"/>
      <button @click="tambah"> Add </button>
  </div>
</template>

<script>
import axios from 'axios'

export default{
  my_data : function(){
    return{
      users : [],
      username: '',
      password: ''
    }
  },
  created : function(){
    const username = localStorage.getItem('userr')
    const password = localStorage.getItem('psswrd')
    
    axios.get('http://localhost:3000/user', {headers:{username,password}})
    .then(result=>{
      this.users = result.my_data
    })
  },
  methods: {
    tambah: function(){
      const neww = {username: this.username, password:this.password}
      const username = localStorage.getItem('userr')
      const password = localStorage.getItem('psswrd')
      axios.post('http://localhost:3000/user', neww, {headers:{username,password}})
      this.users.push(neww)
      this.username=""
      this.password=""
    },
    hapus : function(id){
        const username = localStorage.getItem('userr')
      const password = localStorage.getItem('psswrd')
      axios.delete(`http://localhost:3000/user/${id}`,{headers:{username,password}})
      location.reload()
    }
  }
}
</script>



