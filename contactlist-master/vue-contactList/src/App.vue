<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div id="app">
    
    <Navbar :showLogout="isLoggedIn"/>
    <router-view></router-view>
  </div>
</template>

<script>
import { ref, computed } from 'vue'
import Navbar from '@/components/Navbar.vue'

// Use a ref to keep track of the logged in status
const isLoggedIn = ref(localStorage.getItem('loggedIn') === 'true')

// Define a computed property that returns a boolean indicating if the user is logged in
const showLogout = computed(() => isLoggedIn.value)

function logout() {
  isLoggedIn.value = false
  this.$router.push('/login')
  localStorage.removeItem('loggedIn')
}
</script>

<style>
  body {
    background-color: #222;
    color: #fff;
  }
</style>
