<template>
  <div class="welcome container">
    <p> Welcome Chattie😍🥵</p>
    <SignupForm/>
    <!-- <LoginForm/> -->
  </div>
</template>

<script>
import SignupForm from '../components/SignupForm.vue';
import LoginForm from '../components/LoginForm.vue';
export default {
  components: { SignupForm,LoginForm },
  

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
  padding: 10px;
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
</style>