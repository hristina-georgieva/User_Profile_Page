<script setup>
const props = defineProps({
  userId: {
    type: Number,
    required: true,
  },
})

import { ref, watch } from 'vue'
import EditForm from './EditForm.vue';

const retrievedData = ref({});
const id = ref(props.userId);
const dataIsRetrieved = ref(false);

const notEditMode = ref(true)


function edit(event, newInfo) {
  if (event) {
    notEditMode.value = !notEditMode.value
  }
  if(newInfo) {
    retrievedData.value = newInfo;
  }
}

watch(async () => {
    try {
      const res = await fetch(`https://jsonplaceholder.typicode.com/users/${id.value}`)
      retrievedData.value = (await res.json());
      dataIsRetrieved.value = true;
    } catch (error) {
      console.log(error);
    } 
})

</script>

<template>
  <div class="profile" v-if="notEditMode">
    <h1 class="green">My profile</h1>

    <div v-if="dataIsRetrieved" id="userData">
      <h3><strong>Name:</strong> {{retrievedData.name}}</h3>
      <h3><strong>User name:</strong> {{retrievedData.username}}</h3>
      <h3><strong>Email:</strong> {{retrievedData.email}}</h3>
      <h3><strong>Address:</strong> {{retrievedData.address.street}}, {{retrievedData.address.suite}}, {{retrievedData.address.city}}, {{retrievedData.address.zipcode}}</h3>
      <h3><strong>Lat:</strong> {{ retrievedData.address.geo.lat }}, <strong>Lng:</strong> {{ retrievedData.address.geo.lng }}</h3>
      <h3><strong>Phone:</strong> {{retrievedData.phone}}</h3>
      <h3><strong>Website:</strong> {{retrievedData.website}}</h3>
      <h3><strong>Company:</strong> {{ retrievedData.company.name }}; <strong>Phrase:</strong> {{ retrievedData.company.catchPhrase }}; <strong>Bs:</strong> {{ retrievedData.company.bs }}</h3>
      <button @click="edit">Edit info</button>
    </div>
  </div>
  <div v-else>
    <EditForm :userInfo="retrievedData" :edit="edit" />
  </div>
</template>

<style scoped>
.profile {
  margin-top: 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  /* height: 80vh;   */
  flex-direction: column; 
  gap: 10px;
  background-color: aquamarine;
}

#userData {
  padding: 50px;
}

.green {
  margin-bottom: -20px;
  margin-top: 50px;
}

strong {
  font-weight: bold;
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
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }

  #userData {
    padding: 100px;
  }

  .green {
    margin-bottom: -50px;
    margin-top: 50px;
  }

  button {
    margin-bottom: -50px;
  }
}
</style>
