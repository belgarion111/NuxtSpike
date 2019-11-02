<template>
<v-app :style="{ backgroundImage: 'url(body.jpg)', backgroundPosition: 'center center', backgroundSize: 'cover'}">
    <v-navigation-drawer v-model="drawer" :mini-variant="miniVariant" fixed app src="/menuBackground.jpg">
      <v-list>
        <v-list-item v-for="(item, i) in items" :key="i" :to="item.to" router exact>
          <v-list-item-action>
            <v-icon color="purple darken-2" >{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title  v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
</v-app>
</template>
<script>
import axios from 'axios'

export default {
  middleware: 'authenticated',
  data () {
    return {
      drawer: true,
      fixed: false,
      items: [
            {
                "icon": "person",
                "title": "Tannoy",
                "to":"/person/Tannoy"
            },
            {
                "icon": "person",
                "title": "Sin",
                "to":"/person/Sin"
            }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Bean'
    }
  }
}
</script>

<style scoped>
title {
   background: purple;
}
</style>
