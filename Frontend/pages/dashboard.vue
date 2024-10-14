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
            <label @click = "nameClick">Name</label>
            <label @click = "emailClick">Email</label>
            <label @click = "signupClick">Signup Date</label>
            <label @click = "teamClick">Team</label>
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

</script>
