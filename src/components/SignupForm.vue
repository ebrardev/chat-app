<template>
    <div class="signupform">
  <form @submit.prevent="handleSubmit">
    <input type="text" required placeholder="Username" v-model="displayName" />
    <input type="email" required placeholder="email" v-model="email" />
    <input type="password" required placeholder="password" v-model="password" />
    <button class="signup"> Sign up</button>
  </form>
</div>
</template>

<script>
import { ref } from "vue";
export default {
    setup(){
        const displayName = ref("");
        const email = ref("");
        const password = ref("");
        const handleSubmit = (e) => {
            console.log(displayName.value, email.value, password.value);
        }
        return{
            displayName,
            email,
            password,
            handleSubmit
        }
    

    }

}
</script>

<style>


</style>