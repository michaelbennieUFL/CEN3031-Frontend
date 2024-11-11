<script setup lang="ts">
const message=ref('')
const nameClick=ref(false)
const emailClick=ref(false)
const signupClick=ref(false)
const name=ref('N/A')
const email=ref('N/A')
const username=ref('N/A')
const team= ref('UF Women Club Soccer')
definePageMeta({
  middleware: ['auth-logged-in'],
})
function teamClick(){
  alert('Team cannot be edited')

}

const submit = () => {
  console.log("Submitted", {
    name: name.value,
    email: email.value,
    username: username.value,
    team: team.value
  })
}

function submitbutton(){
  alert('submitted')
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
        <br>
        Build the important stuff.
      </p>
    </div>
    <section class="next-steps-section">
      
        <h1>Profile Settings</h1>

          <!-- Fields -->
          <div>
            <!--Name button-->
            <label @click = "nameClick = true">Name: {{ name }}</label>
            <p></p>
            <!--prompt and input box disapear when on enter event (@keyup.enter)-->
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
                v-if="$auth.user?.picture"
                class="avatar"
                :src="$auth.user?.picture"
                alt="user profile avatar"
                referrerPolicy="no-referrer"
              >
          </div>
    </section>
  </div>
</template>


