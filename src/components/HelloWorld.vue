<template>
  <div>
    <div> Tugas Web </div>
    <ul>
      <li v-for="i in todos" :key="i.id"> {{i.desc}}
        <button @click="hapus(i.id)">X</button>
      </li>
    </ul>
      <input v-model = "myText" name="desc"/>
      <button @click="tambah"> Add </button>
  </div>
</template>

<script>
import axios from 'axios'

export default{
  my_data : function(){
    return{
      todos : [],
      myText: ''
    }
  },
  created : function(){
    axios.get('http://localhost:3000/todo')
    .then(result=>{
      this.todos = result.my_data
    })
  },
  methods: {
    tambah: function(){
      const neww = {desc: this.myText}
      axios.post('http://localhost:3000/todo', neww)
      this.todos.push(neww)
      this.myText=""
    },
    hapus : function(id){
      axios.delete(`http://localhost:3000/todo/${id}`)
      location.reload()
    }
  }
}
</script>



