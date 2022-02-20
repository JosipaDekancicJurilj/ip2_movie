<template>
  <v-app id="inspire">
    <v-app-bar
      app
      color="purple"
      flat
      shrink-on-scroll
    >
          <v-avatar
        :color="$vuetify.breakpoint.smAndDown ? 'dark' : 'transparent'"
        size="32"
      ></v-avatar>

      <v-tabs
        centered
        class="ml-n9"
        color="dark"
      >
        <v-tab
          v-for="link in links"
          :key="link"
          :to="link.path"
        >
          {{ link.text }}
        </v-tab>
      </v-tabs>

      <v-avatar
        class="hidden-sm-and-down"
        color="dark"
        size="32"
      ></v-avatar>

      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Informatički projekt - Filmovi</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    links: [ 
      {text:'Home', path:'/'},
      {text: 'About', path:'/About'},
    ]
  }),
};
</script>
