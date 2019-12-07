<template>
        <v-app :style="{ backgroundImage: 'url(/body.jpg)', backgroundPosition: 'center center', backgroundSize: 'cover' }"  >
          <v-app-bar src="/page-background.jpg" scroll-target="#scrolling-techniques-2" fixed app >
            <v-img src="/logo.png" aspect-ratio="1.5" class="grey lighten-2" max-width="150" max-height="50" ></v-img>
            <v-spacer />
          </v-app-bar>
          <v-navigation-drawer v-model="drawer" :mini-variant="miniVariant" fixed app src="/page-background.jpg" width="170px">
            <v-list>
              <v-list-item v-for="(item, i) in items" :key="i" :to="item.to" router exactn>
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
          <v-footer :fixed="falsetou" app >
            <span>&copy; 2019</span>
          </v-footer>
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
