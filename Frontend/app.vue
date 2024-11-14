<template>
  <header>
    <nav class="nav container">
      <h1 class="text-display-3">
        Team Goals

      </h1>
      <NuxtLink to="./">Home</NuxtLink>
      <NuxtLink to="/memberInfo">Potential Member Information</NuxtLink>
      <NuxtLink to="/dashboard">Settings</NuxtLink>
    
      <div v-if="$auth.loggedIn">
        <div class="profile-blob">
          <img
            v-if="$auth.user.picture"
            class="avatar"
            :src="$auth.user.picture"
            alt="user profile avatar"
            referrerPolicy="no-referrer"
          >
          <div
            v-else
            class="avatar"
          >
            {{ $auth.user?.given_name?.[0] }} {{ $auth.user?.family_name?.[0] }}
          </div>

          <div>
            <p class="text-heading-2">
              {{ $auth.user?.given_name }} {{ $auth.user?.family_name }}
            </p>

            <NuxtLink
              class="text-subtle"
              to="/api/logout"
              external
            >
              Log out
            </NuxtLink>
          </div>
        </div>
      </div>
      <div v-else>
        <NuxtLink
          class="btn btn-ghost sign-in-btn"
          to="/api/login"
          external
        >
          Sign in
        </NuxtLink>
        <NuxtLink
          class="btn btn-dark"
          to="/api/register"
          external
        >
          Sign up
        </NuxtLink>
      </div>
    </nav>
  </header>
  <main><NuxtPage /></main>
  <footer class="footer">
    <div class="container">
      <strong class="text-heading-2">Team Goals</strong>
      <p></p>
      <small class="text-subtle">© 2024 Alea Atkinson, Michael Bennie, Tristan Hendry & Andrea Mueller All rights reserved</small>
    </div>
  </footer>
</template>

<script>
import '~/assets/css/globals.css'
</script>
