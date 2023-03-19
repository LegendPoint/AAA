<template>
  <main>
    <div class="container">
      <div class="welcome-text">
    <h1>WELCOME!!!</h1>
  </div>
      <div class="loginPanel">
        <h1>LOGIN</h1><br/>
        <div>
          <p class="info" >USERNAME</p>
          <input v-model="username" type="text" placeholder="Username">
          <div id="username_empty" >Invalid Username</div>
          <div id="username_incorrect" >Incorrect username or password</div>
          <div>
          <p class="info" placeholder="Password">PASSWORD</p>
        </div>
          <input v-model="password" type="password" placeholder="Password">
          <div id="password_empty" class="input_error">Invalid Password</div>
        </div><br/>
        <h5>NO ACCOUNT? <a href="/register">SIGNUP HERE</a></h5><br/>
        <button type="submit" @click="login">SIGN IN</button>
        <button v-if="isLoggedIn" @click="logout">LOGOUT</button>
      </div>
  
</div>
  </main>
</template>

<script>
import axios from 'axios'

export default{
  data() {
    return {
      username: '',
      password: '',
      isLoggedIn: false,
    }
  },
  methods: {
    
    async login() {
      let user_empty = document.getElementById('username_empty')
      let pass_empty = document.getElementById('password_empty')
      let user_incorrect = document.getElementById('username_incorrect')

      user_empty.style.display = (this.username.length == 0) ? "block" : "none";
      pass_empty.style.display = (this.password.length == 0) ? "block" : "none";
      
      
      let result = axios.get(`http://localhost:5001/auser?username=${this.username}&password=${this.password}`)
      .then((result) => {
        console.log(result.data);
        //each user/pass should be unique, thus 1
        if(result.data.length == 1){
          this.isLoggedIn = true;
          this.$router.push('/contactlist');
        }
        else{
          if(user_empty.style.display == "none" && pass_empty.style.display == "none"){
            user_incorrect.style.display = "block"
          } else {
            user_incorrect.style.display = "none"
          }
        }
      })
      .catch((error) => {
        console.error(error);
      });
    },
    
    logout() {
      this.isLoggedIn = false;
      this.$router.push('/');
    }
  },
};

</script>

<style>

::placeholder{
  opacity: 50%;
}

p.info {
  text-align: left;
  margin-top: 10%;
}

#username_empty,
#password_empty{
  
  margin-left: 3px;
  opacity: 60%;
  font-size: 80%;
  text-align: left;
  color: red;
  display: none;
}

#username_incorrect{
  margin-left: 3px;
  opacity: 60%;
  font-size: 75%;
  text-align: left;
  color: red;
  display: none;
}

.container{
    display: left;
    font-family: 'Montserrat', sans-serif;
    color: black;
    background-color: rgb(220, 227, 233);
    border-radius: 16px 16px 16px 16px;
    padding: 100%;
    width: 100%;
    
}
  .loginPanel {
    font-family: 'Montserrat', sans-serif;
    margin-left:0px;
    margin-right:0px;
    width: 100%;
    text-align: center;
    padding-left:50px;
  }
  .welcome-text {
  font-family: 'Montserrat', sans-serif;
  text-align: center;
  margin-bottom: 10px;
  padding:50px;
 
}
  


</style>
