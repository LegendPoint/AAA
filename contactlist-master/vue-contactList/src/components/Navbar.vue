<template>
    <nav class="navbar navbar-expand-lg navbar-light" style="background-color: #e3f2fd;">
       
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
      
        
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item">
          <router-link to="/contactlist" class="nav-link">CONTACT LIST</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/register" class="nav-link">REGISTER</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/" class="nav-link">LOGIN</router-link>
        </li>
        
      </ul>
          
        </div>
      </nav>
    </template>
    
    <script>
import Register from '@/views/Register.vue'
import Login from '@/views/Login.vue'

export default {
  components: {
    Register,
    Login
  },
  methods: {
    goToHome() {
      this.$router.push('/')
    },
    goToSignUp() {
      this.$router.push('/register')
    },
    goToSignIn() {
      this.$router.push('/login')
    }
  }
}
</script>
    
    
    
    
    <style>
    .navbar {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
      }
    </style>
