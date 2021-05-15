<template>
  <v-app>
    <v-app-bar dark fixed app>
      <v-toolbar-title  />
      <h2>
      هجري .كوم

      </h2>
      <v-spacer />
      <v-toolbar-title>Hijri.com</v-toolbar-title>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>

    <v-footer app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
     
    }
  },
}
</script>
