<script lang="ts">
import { ref, onMounted, defineComponent } from 'vue'
import axios from 'axios'

export default defineComponent({
  setup() {
    const players = ref<{ id: number; name: string }[]>([])

    onMounted(async () => {
      try {
        const response = await axios.get('http://127.0.0.1:5002/user/players', {
          withCredentials: true,
        })
        if (response.status === 200) {
          players.value = response.data
        } else {
          console.error('Unexpected response status:', response.status)
        }
      } catch (error) {
        console.error('Error fetching players:', error)
      }
    })

    return {
      players
    }
  }
})
</script>

<template>
  <div class="container">
    <header>
      <h1> Player Statistics Page </h1>
    </header>
    <section>
      <h2>All Players</h2>
      <ul>
        <li v-for="player in players" :key="player.id">
          {{ player.name }}
        </li>
      </ul>
    </section>
  </div>
</template>
