<template>
  <div class="container mt-5">
    <h2>Login</h2>
    <input v-model="username" placeholder="Enter username" class="form-control my-2" />
    <input type="password" v-model="password" placeholder="Enter password" class="form-control my-2" />
    <button class="btn btn-primary" @click="login">Login</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const username = ref('')
const password = ref('')
const router = useRouter()

const login = () => {
  if (username.value && password.value) {
    localStorage.setItem('isAuthenticated', 'true')
    router.push('/home')
  } else {
    alert('Please enter dummy credentials')
  }
}
</script>

<style>
.container {
  max-width: 400px;
  margin: auto;
}
</style>
