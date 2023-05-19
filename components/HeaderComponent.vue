<template>
    <div class="header-container">
        <img @click="goHome()" class="logo-image" src="https://i.ibb.co/QF9NmXb/daf1cd39-5d9c-4660-b505-8b6bc63fe776.jpg" alt="logo">
        <p @click="logout()">Log out</p>
    </div>
</template>

<script>
export default {
  name: 'HeaderComponent',
  methods: {
    logout () {
      this.$router.push('/')
    },
    goHome () {
      this.$router.push('/HomePage')
    }
  }

}
</script>
