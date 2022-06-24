<template>
  <v-app-bar
      app
      color="primary"
      dark
  >
    <div class="d-flex align-center">
      <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
      />

      <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
      />
    </div>

    <v-spacer></v-spacer>

    <v-btn
        @click="logout"
        target="_blank"
        text
    >
      <span class="mr-2">Logout</span>
      <v-icon>mdi-open-in-new</v-icon>
    </v-btn>
  </v-app-bar>
</template>

<script>
import {getAuth, signOut} from 'firebase/auth'

export default {
  name: "NavBar",

  methods: {
    logout() {
      const auth = getAuth()
      signOut(auth)
          .then(() => {
            // Sign-out successful.
            this.$router.push('/login')
          })
          .catch((error) => {
            // An error happened.
            console.log(error)
          })
    }
  },
}
</script>

<style scoped>

</style>