<template>
  <v-app>
    <v-app-bar dark fixed app>
      <v-toolbar-title />
      <h1>هجري .كوم</h1>
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
   <span class="effra-font">برعاية لطيفة من الرائعين في: <a class="effra-font" href="https://wasetshera.com/?myad=53198" >وسيط شراء</a> و <a class="effra-font" href="https://knaree.com/" >كناري</a> و <a class="effra-font" href="https://rmmmz.com/" >رمز</a></span>	
		
          <br />
          للإتصال بنا:
          <a href="mailto:Hijre@inboxeen.com">Hijre@inboxeen.com</a>

          <br />
          جميع الحقوق محفوظة - موقع هجري 2022 ©
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
*{
  font-family: "Graphik";
  font-weight: 300;
}
.theme--dark.v-app-bar.v-toolbar.v-sheet {
	background-color: #2e7d32 !important;
	border-color: #2e7d32 !important;
}
.v-toolbar__title {
	font-size: 24px;
	line-height: 1.5;
	overflow: hidden;
	text-overflow: ellipsis;
	white-space: nowrap;
	font-weight: bold;
}
.v-application a {
	color: #2e7d32 !important;
}
@media screen and (max-width: 900px){
.v-btn--fab{
left: 40px;
}
}
</style>
