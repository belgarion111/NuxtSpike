<template>
  <v-layout column justify-center align-center >
    <v-flex xs12 sm8 md6 >
          <v-card
            class="mx-auto"
            max-width="800"
          >
            <v-img
              class="white--text align-end"
              height="400px"
              :src="image"
            >
              <v-card-title>User {{ name }}</v-card-title>
            </v-img>

            <v-card-subtitle class="pb-0">{{ name }}</v-card-subtitle>

            <v-card-text class="text--primary">
              <div>Class {{ type }}</div>
              <div>Level {{ level }}</div>
            </v-card-text>

            <v-card-actions>
              <v-btn
                color="orange"
                text
              >
                Share
              </v-btn>

              <v-btn
                color="orange"
                text
              >
                Explore
              </v-btn>
            </v-card-actions>
          </v-card>
    </v-flex>
  </v-layout>
</template>

<script>

export default {
  layout: 'inspire',
  data () {
    return {
      name  : '',
      type : '' ,
      level : 0 ,
      image : ''
    }  
  },
  mounted: function () {
    debugger
    this.$axios.$get(`/person/${this.$route.params.pathMatch}.json`)
    .then((res) => {
      this.name = res.name
      this.type = res.class
      this.level = res.level
      this.image = res.image
    }).catch(error => {
       console.log(error)
    });
    console.log(this.name);
 }
}
</script>