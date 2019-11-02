<template>
<v-app :style="{ backgroundImage: 'url(body.jpg)', backgroundPosition: 'center center', backgroundSize: 'cover'}">
  <v-layout column justify-center align-center >
    <v-flex xs12 sm8 md6 >
        <div>User {{ $route.params.pathMatch}}</div>
    </v-flex>
  </v-layout>
</v-app>
</template>

<script>

export default {
  layout: 'inspire'
}
</script>