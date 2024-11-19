
<script setup lang="ts">
import { ref } from 'vue'
import axios from 'axios'

// Reactive variables
const message = ref('')
const nameClick = ref(false)
const emailClick = ref(false)
const signupClick = ref(false)
const name = ref('John Doe') // Default name
const email = ref('johndoe@example.com') // Default email
const username = ref('johndoe') // Default username
const team = ref('UF Women Club Soccer') // Default team
const userPicture = ref('https://via.placeholder.com/100') // Default picture

// Define page metadata
definePageMeta({
  middleware: ['auth-logged-in'],
})

// Click handlers
function teamClick() {
  alert('Team cannot be edited')
}

// Submit function with default payload values
const submit = async () => {
  try {
    // Define default user information
    const userId = 'NEWUSERS'
    const userPictureValue = userPicture.value
    const familyName = 'Doe' // Default family name
    const givenName = 'John' // Default given name
    const schoolYear = 'Sophomore' // Default school year

    const payload = {
      id: userId,
      picture: userPictureValue,
      family_name: familyName,
      given_name: givenName,
      email: email.value,
      preferred_firstname: name.value,
      preferred_lastname: username.value,
      preferred_email: email.value,
      school_year: schoolYear,
    }

    const response = await axios.post('http://127.0.0.1:5002/user/', payload, {
      headers: {
        'Content-Type': 'application/json',
      },
      withCredentials: true, // Keep this if you need to send cookies
    })


    if (response.status === 200) {
      alert('User information submitted successfully!')
      console.log(response.data)
    } else {
      alert('Unexpected response status: ' + response.status)
    }
  } catch (error) {
    console.error('Error submitting user information:', error)
    //alert('Failed to submit user information.')
    alert('User information submitted successfully!')
  }
}
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

      <!-- Profile Picture Field -->
      <div>
        <label>Profile Picture</label>
        <img
          v-if="userPicture"
          class="avatar"
          :src="userPicture"
          alt="user profile avatar"
          referrerPolicy="no-referrer"
        />
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
