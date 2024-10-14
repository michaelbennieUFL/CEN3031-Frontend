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
            <label @click = "nameClick = true">Name</label>
            <label @click = "emailClick = true">Email</label>
            <label @click = "signupClick = true">Signup Date</label>
            <label @click = "teamClick = true">Team</label>
            <p>What is your name: {{ message }}</p>
            <input
                v-if = "nameClick"
                v-model = "Yourname"
                type = "text"
                placeholder = "Your Name"
                @keyup.enter = "submit"
                   />
            <input
                v-if = "emailClick"
                v-model = "email"
                type = "email"
                placeholder = "email@youremail.com"
                @keyup.enter = "submit"
                   />
            <input
                v-if = "signupClick"
                v-model = "signup"
                type = "text"
                placeholder = "username"
                @keyup.enter = "submit"
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

<script setup lang="ts">
definePageMeta({
  middleware: ['auth-logged-in'],
})
function teamClick(){
  return "you clicked the team"

}
const submit = () => {
  console.log("Submitted", {
    name: yourName.value,
    email: email.value,
    signup: signup.value,
    team: team.value
  })
}

</script>
