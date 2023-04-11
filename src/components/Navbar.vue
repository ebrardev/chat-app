<template>
  <nav >
    <div>
        <p>Welcome {{ user.displayName }} </p>
        <p  class="email" >Currently logged in as... {{ user.email }}</p>
    </div>
    <button @click="handleClick" class="my-navbar-button">Logout</button>

  </nav>
</template>

<script>
import useLogout from '../composables/useLogout';
import getUser from '../composables/getUser';
export default {
    setup() {
        const {logout,error} = useLogout();
        const {user} = getUser();
        const handleClick = async () => {
            await logout();
            if(!error.value) {
                window.alert("Çıkış yapıyorsunuz..!");
                window.location.href = "/";
            }
        }
        return {
            handleClick,user 
        }
    }

}
</script>

<style >
 nav{
  padding: 20px;

  display: flex;
  justify-content: space-between;
  align-items: center;
 }
 nav p {
  margin: 2px auto;
  font-size: 16px;
  color: #444;
  text-align: left;

 }
 nav p.email{
  font-size: 14px;
  color: #888
 }
 
 .my-navbar-button {
    background-color:rgb(5, 5, 128);
    margin: 10px;
    padding: 10px 15px;
    text-align: center;
    align-items: center;
    text-transform: uppercase;
    transition: 0.5s;
    background-size: 200% auto;
    color: white;            
    box-shadow: 0 0 20px #eee;
    border-radius: 10px;
    display: inline-block;
    font-size: 12px;
}
 
.my-navbar-button:hover {
    background-color: red;
}
 
</style>