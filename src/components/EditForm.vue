<script setup>
const props = defineProps({
  userInfo: {
    type: Object,
    required: true,
  },
  edit: {
    type: Function,
    required: true
  }
})

import { ref } from 'vue'

const name = ref(props.userInfo.name);
const username = ref(props.userInfo.username);
const email = ref(props.userInfo.email);
const address = ref(props.userInfo.address);
const phone = ref(props.userInfo.phone);
const website = ref(props.userInfo.website);
const company = ref(props.userInfo.company);


function save(event) {
  if (event) {
    if(!name.value){
      alert('Name cannot be empty!');
      name.value = props.userInfo.name
      throw new Error('Name is empty');
    }
    if(!username.value){
      alert('Username cannot be empty!');
      username.value = props.userInfo.username
      throw new Error('Username is empty');
    }
    if(!email.value){
      alert('Email cannot be empty!');
      email.value = props.userInfo.email
      throw new Error('Email is empty');
    }
    if(!address.value){
      alert('Address cannot be empty!');
      address.value = props.userInfo.address
      throw new Error('Address is empty');
    }
    if(!phone.value){
      alert('Phone cannot be empty!');
      phone.value = props.userInfo.phone
      throw new Error('Phone is empty');
    }
    if(!website.value){
      alert('Website cannot be empty!');
      website.value = props.userInfo.website
      throw new Error('Website is empty');
    }
    if(!company.value){
      alert('Company cannot be empty!');
      company.value = props.userInfo.company
      throw new Error('Company is empty');
    }
    const updatedInfo = {
      name,
      username,
      email,
      address,
      phone,
      website,
      company
    }
    props.edit(event, updatedInfo);
  }
}

</script>

<template>
  <div class="editData">
    <h1 class="green">Edit profile</h1>
    <div id="all">
      <div id="left">
        <h3>Name: </h3>
        <input id="nameInput" v-model="name" />
        <h3>User name:</h3>
        <input id="usernameInput" v-model="username" />
        <h3>Email:</h3>
        <input id="emailInput" v-model="email" />
        <h3>Address:</h3>
        <ul>
          <li>
            <h3>Street:</h3>
            <input id="streetInput" v-model="address.street" />
          </li>
          <li>
            <h3>Suite:</h3>
            <input id="suiteInput" v-model="address.suite" />
          </li>
          <li>
            <h3>City:</h3>
            <input id="cityInput" v-model="address.city" />
          </li>
          <li>
            <h3>Zipcode:</h3>
            <input id="zipcodeInput" v-model="address.zipcode" />
          </li>
          <li>
            <h3>Lat:</h3>
            <input id="latInput" v-model="address.geo.lat" />
          </li>
          <li>
            <h3>Lng:</h3>
            <input id="lngInput" v-model="address.geo.lng" />
          </li>
        </ul>
      </div>
      <div id="right">
        <h3>Phone:</h3>
        <input id="phoneInput" v-model="phone" />
        <h3>Website:</h3>
        <input id="websiteInput" v-model="website" />
        <h3>Company:</h3>
        <ul>
          <li>
            <h3>Name:</h3>
            <input id="companyNameInput" v-model="company.name"/>
          </li>
          <li>
            <h3>Catch phrase:</h3>
            <input id="catchPhraseInput" v-model="company.catchPhrase"/>
          </li>
          <li>
            <h3>Bs:</h3>
            <input id="bsInput" v-model="company.bs"/>
          </li>
        </ul>
      </div>
    </div>
    <button @click="save">Save</button>
  </div>
</template>

<style scoped>

.editData {
  margin-top: 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  /* height: 80vh;   */
  flex-direction: column; 
  gap: 10px;
  background-color: aquamarine;
}

h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: left;
}

button {
  font-size: 1.0rem;
  padding: 10px 30px;
  display: block; 
  margin: 20px auto 0;
  background-color: hsla(160, 100%, 37%, 1); 
  margin-bottom: 50px
}


@media (min-width: 1024px) {
  #all {
    display: flex;
  }

  #left {
    margin-right: 50px;
  }

  #right {
    margin-left: 50px;
  }
}
</style>
