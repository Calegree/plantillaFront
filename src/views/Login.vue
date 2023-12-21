<script setup>
import {ref} from 'vue';
import axios from 'axios'

const loginUser = async () => {
    try {
        const formData = {
            username:username.value,
            password:password.value
        }
        console.log(formData);

        const response = await axios.post(
            "http://localhost:8080/auth/login",
            formData
        );
        console.log(response.data);
    } catch (error) {
        console.error("Error al enviar el login: ", error)
    }

}


const username = ref("");
const password = ref("");


</script>

<template>
  <div class="container pageContainer">
    <form @submit.prevent="loginUser">
      <div class="input-group mb-3 inputText">
        <span class="input-group-text" id="inputGroup-sizing-default"
          >username</span
        >
        <input
        v-model="username"
          type="text"
          class="form-control"
          aria-label="Sizing example input"
          aria-describedby="inputGroup-sizing-default"
        />
      </div>
      <div class="input-group mb-3 inputText">
        <span class="input-group-text" id="inputGroup-sizing-default"
          >password</span
        >
        <input
        v-model="password"
          type="text"
          class="form-control"
          aria-label="Sizing example input"
          aria-describedby="inputGroup-sizing-default"
        />
      </div>
      <button type="submit" class="btn btn-primary boton">Submit</button>
    </form>
  </div>
</template>

<style>
.pageContainer {
  margin-top: 15%;
}
.inputText {
  width: 300px;
  margin-top: 50px;
  margin-bottom: 30px;
  margin-left: 35%;
}
.boton {
  width: 300px;
  margin-left: 35%;
}
</style>
