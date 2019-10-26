<template>
<v-app :style="{ backgroundImage: 'url(body.jpg)', backgroundPosition: 'center center', backgroundSize: 'cover'}">
  <v-layout column justify-center align-center >
    <v-flex xs12 sm8 md6 >
      <v-card :style="{opacity:0.8}" width="400">
        <v-card-title class="headline">
            Login
        </v-card-title>
        <v-card-text>
          <loginForm /> 
        </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</v-app>
</template>

<script>
import LoginForm from '~/components/LoginForm.vue'

export default {
  components: {
    LoginForm
  }
}
</script>