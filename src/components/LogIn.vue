<script setup>
import { ref, watch } from 'vue'
import ProfileView from './ProfileView.vue'


const enteredUserName = ref('');
const foundUser = ref({});
const notLogged = ref(true);

function log(event) {
  if (event) {
    watch(async () => {
      try {
        const res = await fetch('https://jsonplaceholder.typicode.com/users/')
        foundUser.value = (await res.json()).find(el => el.username===enteredUserName.value);
        if(foundUser.value) {
          notLogged.value = false;
        } else {
          alert('Username not found!');
        }
      } catch (error) {
        alert('Username not found!');
        console.log(error);
      } 
    })
  }
}
</script>

<template>
  <div class="login" v-if="notLogged">
    <div>
      <h2>Enter username:</h2>
      <input id="userNameInput" v-model="enteredUserName" />
      <button @click="log">Log in</button>
    </div>
  </div>
  <div v-else>
    <ProfileView :userId="foundUser.id" />
  </div>
</template>

<style scoped>
.login {
  margin-top: 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 80vh;  
  flex-direction: column; 
  gap: 10px;
  background-color: aquamarine;
}

button {
  font-size: 1.0rem;
  padding: 10px 30px;
  display: block; 
  margin: 20px auto 0;
  background-color: hsla(160, 100%, 37%, 1); 
}

#userNameInput {
  height: 35px
}
</style>
