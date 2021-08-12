<template>
  <v-app>
    <v-app-bar dark fixed app>
      <v-toolbar-title />
      <h2>هجري .كوم</h2>
      <v-spacer />
      <v-toolbar-title>Hijre.com</v-toolbar-title>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>

    <v-footer app>
      <v-row>
        <v-col style="text-align: center">
          الموقع برعاية :

          <a href="https://wasetshera.com?myad=53198"> وسيط شراء من الإنترنت</a>
          <br />
          للإتصال بنا:
          <a href="mailto:Hijre@inboxeen.com">Hijre@inboxeen.com</a>

          <br />
          جميع الحقوق محفوظة - موقع هجري 2021 ©
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {}
  },
}
</script>
<style>
* {
  font-family: 'Tajawal', Open-Sans;
  font-weight: 400;
}
</style>
