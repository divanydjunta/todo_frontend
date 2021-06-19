<template>
  <router-link to="/">Hal Auth</router-link><br>
  <router-link to="/todo">Hal Todo</router-link>
  <router-link to="/user">Hal User</router-link>
  <router-view></router-view>
</template>

<script setup>
import todo from './components/todo.vue'
import user from './components/user.vue'

// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
</script>

