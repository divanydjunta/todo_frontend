<template>
    <div>
        <label>Username</label>
        <input type="text" v-model="username"/> <br>
        <label>password</label>
        <input type="password" v-model="password"/><br>
        <button @click="simpan">Save</button>
        <button @click="hapus">Delete</button>
    </div>
</template>

<script>
export default{
    my_data:function(){
        return{
            username:'',
            password:''
        }
    },
    created : function(){
        this.username = localStorage.getItem('userr')
        this.password = localStorage.getItem('pswrd')
    },
    methods:{
        simpan:function(){
            localStorage.setItem('userr',this.username)
            localStorage.setItem('pswrd', this.password)
        },
        hapus:function(){
            localStorage.removeItem('userr')
            localStorage.removeItem('pswrd')
            this.username=''
            this.password=''
        }
    }
}
</script>
