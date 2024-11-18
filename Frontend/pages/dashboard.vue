<script setup lang="ts">
import { ref } from 'vue'

const message = ref('')
const nameClick = ref(false)
const emailClick = ref(false)
const signupClick = ref(false)
const name = ref('N/A')
const email = ref('N/A')
const username = ref('N/A')
const team = ref('UF Women Club Soccer')
const userPicture = ref('https://t4.ftcdn.net/jpg/02/15/84/43/360_F_215844325_ttX9YiIIyeaR7Ne6EaLLjMAmy4GvPC69.jpg')

definePageMeta({
  middleware: ['auth-logged-in'],
})

function teamClick() {
  alert('Team cannot be edited')
}

const submit = () => {
  console.log("Submitted", {
    name: name.value,
    email: email.value,
    username: username.value,
    team: team.value,
    userPicture: userPicture.value // Log user picture if needed
  })
}

function submitbutton() {
  alert('submitted')
}
</script>

<template>
  <div class="general">
  <div class="container">
    <div class="welcome">
    
      <p class="text-display-2">
        Welcome Back!
      </p>
    </div>
    <section class="next-steps-section">
        <h1>Profile Settings</h1>
          <br>
          <!-- Fields -->
          <div>
            <!--Name button-->
            <label @click = "nameClick = true">Name: {{ name }}</label>
            <p></p>
            <!--prompt and input box disapear on enter event (@keyup.enter)-->
            <p v-show="nameClick">What is your name: </p>
            <input
                v-show = "nameClick"
                v-model = "name"
                type = "text"
                placeholder = "Your Name"
                @keyup.enter = "nameClick=false"
                   />
            <p></p>
            <!--Team Button-->
            <label @click = "teamClick">Team: {{ team }}</label>
            <p></p>
            <!--Email button-->
            <label @click = "emailClick = true">Email: {{ email }}</label>
            <p v-show="emailClick">What is your email: </p>
            <input
                v-show = "emailClick"
                v-model = "email"
                type = "email"
                placeholder = "email@youremail.com"
                @keyup.enter = "emailClick=false"
                   />
            <p></p>
            <!--Username button-->
            <label @click = "signupClick = true">Username:{{ username }}</label>
            <p v-show="signupClick">What is your preferred username: </p>
            <input
                v-show = "signupClick"
                v-model = "username"
                type = "text"
                placeholder = "username"
                @keyup.enter = "signupClick=false"
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
