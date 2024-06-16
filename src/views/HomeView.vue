<script setup>
import { useAuthStore } from '@/stores/auth'
import { useRouter } from 'vue-router'

const auth = useAuthStore()
const router = useRouter()


auth.me()

async function logout(){
  await auth.logout()
  router.push({ name: 'login' })
}
</script>

<template>
  <main>
    <div v-if="auth.user">
      <span>
        <h2>Welcome, {{ auth.user.email }}!</h2>
      </span>
      <form @submit.prevent="logout">
        <button type="submit">Logout</button>
      </form>
    </div>
    <div v-else>
      <h2>No user found.</h2>
    </div>
  </main>
</template>
