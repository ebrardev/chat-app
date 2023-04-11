<template>
    <div class="login">
    <form @submit.prevent="handleSubmit">

      <input type="email" required placeholder="email" v-model="email" />
      <input type="password" required placeholder="password" v-model="password" />
      <div class="error">{{ error }}</div>
      <button class="loginbutton"> Login </button>

    </form>
</div>
  </template>
  
  <script>
  import { ref } from "vue";
  import useLogin from "../composables/useLogin";
  export default {
      setup(props,context){
          
          const email = ref("");
          const password = ref("");
          const {error,login} = useLogin()
          const handleSubmit = async() => {
            await login(email.value, password.value)

            if(!error.value) {
              context.emit("login")
            }
           
          }
          return{
     
              email,
              password,
              handleSubmit,
                error
          }
      
  
      }
  
  }
  </script>
  
  <style>

  .loginbutton{
   
    background-image: linear-gradient(to right, #ff6e7f 0%, #bfe9ff  51%, #ff6e7f  100%);
    margin: 10px;
    padding: 15px 45px;
    text-align: center;
    align-items: center;
    text-transform: uppercase;
    transition: 0.5s;
    background-size: 200% auto;
    color: white;            
    box-shadow: 0 0 20px #eee;
    border-radius: 10px;
    display: inline-block;
  }

  .loginbutton:hover {
    background-position: right center; /* change the direction of the change here */
    color: #fff;
    text-decoration: none;
  }
 
  
  
  </style>