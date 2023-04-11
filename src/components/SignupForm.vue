<template>
    <div class="signupform">
  <form @submit.prevent="handleSubmit">
    <input type="text" required placeholder="Username" v-model="displayName" />
    <input type="email" required placeholder="email" v-model="email" />
    <input type="password" required placeholder="password" v-model="password" />
     <div class="error">{{ error }}</div>
    <button class="signup"> Sign up</button>
  </form>
</div>
</template>

<script>
import { ref } from "vue";
import useSignup from "../composables/useSignup";
export default {
    setup(props,context){
        const {error,signup} = useSignup();
        const displayName = ref("");
        const email = ref("");
        const password = ref("");
        const handleSubmit =async () => {
         await signup(email.value, password.value, displayName.value)
          if(!error.value) {
            context.emit("signup")
          }
        }
        return{
            displayName,
            email,
            password,
            handleSubmit,
            error
        }
    

    }

}
</script>

<style>

.signup{
   
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

 .signup:hover {
   background-position: right center; /* change the direction of the change here */
   color: #fff;
   text-decoration: none;
 }

</style>