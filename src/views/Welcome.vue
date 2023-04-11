<template>
  <div class="welcome container">
    <p> Welcome Chattie😍🥵</p>
    <div v-if="showLogin">
      <h2>Login</h2>
      <LoginForm @login="enterChat" />
      <p>Don't have an account? <span class="chatspan" @click="showLogin=false">Signup</span></p>
  

    </div>
    <div v-else>
      <h2>Sign Up</h2>
      <SignupForm @signup= "logins" />
      <p>Already have an account? <span class="chatspan" @click="showLogin=true">Login</span></p>
    </div>
   
    <!-- <LoginForm/> -->
  </div>

  
</template>

<script>
import SignupForm from '../components/SignupForm.vue';
import LoginForm from '../components/LoginForm.vue';
import { ref } from 'vue';
import {useRouter} from 'vue-router';
export default {
  components: { SignupForm,LoginForm },
  setup() {
  const showLogin = ref(true)
  const router = useRouter()

  const enterChat = () => {
    router.push({name: 'chatroom'})
  }
  const logins = () =>{
    showLogin.value = true
}

  return{showLogin,enterChat,logins}
  },
  

}
</script>

<style>

.welcome  {
    text-align: center;
    padding: 20px;
 

}

.welcome form {
  widows: 300px;
  margin: 20px auto;
}
.welcome label {
  display: block;
  margin:20px 0 10px;
}
.welcome input {
  width: 100%;
  padding: 10px 5px;
  border: 1px solid #ccc;
  border-radius: 20px;
  outline: none;
  color: blue;
  margin: 10px auto;
}

.welcome button{
  margin-top: 10px;
  padding: 10px;
  background-color: blue;
  color: white;
  border: none;
  border-radius: 6px;
  outline: none;
  
}
.chatspan{
  cursor: pointer;
  color: rgb(129, 89, 196);
  text-decoration: underline;
  font-weight: bold;
  
  
}
.chatspan:hover{
  color: blue;
}

</style>