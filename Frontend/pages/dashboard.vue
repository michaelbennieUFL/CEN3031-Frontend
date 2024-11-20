
<script setup lang="ts">
import { ref, onMounted } from 'vue'
import axios from 'axios'
import { useNuxtApp } from '#app' // Import useNuxtApp to access $auth

// Access $auth
const { $auth } = useNuxtApp()

// Reactive variables
const message = ref('')
const nameClick = ref(false)
const emailClick = ref(false)
const signupClick = ref(false)
const name = ref('')
const email = ref('')
const username = ref('')
const team = ref('')
const userPicture = ref('')

const userId = ref('')

// Define page metadata
definePageMeta({
  middleware: ['auth-logged-in'],
})

// Click handlers
function teamClick() {
  alert('Team cannot be edited')
}

// On page load, fetch user data
onMounted(async () => {
  // Set the userId from $auth.user
  userId.value = $auth.user?.id || 'NEWUSERS'

  try {
    const response = await axios.get(`http://127.0.0.1:5002/user/${userId.value}`, {
      withCredentials: true,
    });
    if (response.status === 200) {
      const data = response.data;
      name.value = data.preferred_firstname || data.given_name || '';
      username.value = data.preferred_lastname || data.family_name || '';
      email.value = data.preferred_email || data.email || '';
      userPicture.value = data.picture || '';
      team.value = data.team || 'UF Women Club Soccer';
    }
  } catch (error) {
    if (error.response && error.response.status === 404) {
      // User not found, set values from Kinde
      name.value = $auth.user?.given_name || '';
      username.value = $auth.user?.family_name || '';
      email.value = $auth.user?.email || '';
      userPicture.value = $auth.user?.picture || '';
      team.value = 'UF Women Club Soccer';
    } else {
      console.error('Error fetching user information:', error);
    }
  }
});

// Submit function
const submit = async () => {
  try {
    const payload = {
      id: userId.value,
      picture: userPicture.value,
      family_name: username.value,
      given_name: name.value,
      email: email.value,
      preferred_firstname: name.value,
      preferred_lastname: username.value,
      preferred_email: email.value,
      school_year: 'Sophomore', // Or get from a reactive variable
      team: team.value,
    };

    const response = await axios.post('http://127.0.0.1:5002/user/', payload, {
      headers: {
        'Content-Type': 'application/json',
      },
      withCredentials: true,
    });

    if (response.status === 200) {
      alert('User information submitted successfully!');
      console.log(response.data);
    } else {
      alert('Unexpected response status: ' + response.status);
    }
  } catch (error) {
    console.error('Error submitting user information:', error);
    alert('Failed to submit user information.');
  }
};
</script>

<template>
  <div class="container">
    <div class="card start-hero">
      <p class="text-body-2 start-hero-intro">
        Woohoo!
      </p>
      <p class="text-display-2">
        Your authentication is all sorted.
        <br />
        Build the important stuff.
      </p>
    </div>
    <section class="next-steps-section">
      <h1>Profile Settings</h1>

      <!-- Fields -->
      <div>
        <!-- Name Field -->
        <label @click="nameClick = true">Name: {{ name }}</label>
        <p></p>
        <p v-if="nameClick">What is your name:</p>
        <input
          v-if="nameClick"
          v-model="name"
          type="text"
          placeholder="Your Name"
          @keyup.enter="nameClick = false"
        />
        <p></p>

        <!-- Team Field -->
        <label @click="teamClick">Team: {{ team }}</label>
        <p></p>

        <!-- Email Field -->
        <label @click="emailClick = true">Email: {{ email }}</label>
        <p v-if="emailClick">What is your email:</p>
        <input
          v-if="emailClick"
          v-model="email"
          type="email"
          placeholder="email@youremail.com"
          @keyup.enter="emailClick = false"
        />
        <p></p>

        <!-- Username Field -->
        <label @click="signupClick = true">Username: {{ username }}</label>
        <p v-if="signupClick">What is your preferred username:</p>
        <input
          v-if="signupClick"
          v-model="username"
          type="text"
          placeholder="username"
          @keyup.enter="signupClick = false"
        />
      </div>

      <div>
        <label>Profile Picture</label>
        <img
          v-if="userPicture"
          class="avatar"
          :src="userPicture"
          alt="user profile avatar"
          referrerPolicy="no-referrer"
        >
      </div>
      <!-- Submit Button -->
      <div class="submit-section">
        <button @click="submit" class="btn btn-primary">
          Submit
        </button>
      </div>
    </section>
  </div>
</template>

<style scoped>
.container {
  /* Your styles here */
}
.submit-section {
  margin-top: 20px;
}
.btn {
  padding: 10px 20px;
  cursor: pointer;
}
.btn-primary {
  background-color: #007bff;
  color: white;
  border: none;
}
.btn-primary:hover {
  background-color: #0056b3;
}
.avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
}

</style>

<style>
.home{
  color:black;
}
.settings{
  color:#FA4616;
}
</style>
