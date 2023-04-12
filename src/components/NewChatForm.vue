<template>
  <form>
    <textarea
      placeholder="Type a message and hit enter to send..."
      v-model="message"
      @keypress.enter.prevent="handleSend"
    ></textarea>
    <div class="error">{{ error }}</div>
    <button @click.prevent="handleSend">Gönder</button>
  </form>
</template>
<script>
import { ref } from "vue";
import getUser from "../composables/getUser";
import useCollection from "../composables/useCollection";
import { timestamp } from "../firebase/config";
export default {
  setup() {
    const { user } = getUser();
    const { addDoc, error } = useCollection("messages");
    const message = ref("");
    const handleSend = async () => {
  const chat = {
    name: user.value.displayName,
    message: message.value,
    createdAt: timestamp(),
  };
  await addDoc(chat);
  if (!error.value) {
    message.value = "";
  }
};

    const handleSubmit = async () => {
      const chat = {
        name: user.value.displayName,
        message: message.value,
        createdAt: timestamp(),
      };
      await addDoc(chat);
      if (!error.value) {
        message.value = "";
      }
    };
    return { message, handleSubmit, error };
  },
};
</script>

<style scoped>
form {
  margin: 10px;
}
textarea {
  width: 100%;
  max-width: 100%;
  margin-bottom: 10px;
  padding: 10px;
  box-sizing: border-box;
  border: 0;
  border-radius: 20px;
  font-family: inherit;
  outline: none;
}
button{
  padding: 10px;
  border-radius: 10px;
  border: 1 px solid transparent;
  cursor: pointer;
  margin-bottom: 5px;
  display: block;
  margin-left: auto;
  margin-right: 0;
  background-color: #f2f2f2;
  color: #2f2f2f;
  font-weight: bold;
  font-size: 14px;
  transition: all 0.3s ease;
  


}
button:hover{
  background-color: #0c9e1a;
  color: white;
}
</style>