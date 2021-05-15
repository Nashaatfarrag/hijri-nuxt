<template>
  <v-row>
    <v-col :class="textAlign">
      <p>{{ text }}</p></v-col
    >
    <v-col cols="1">
      <v-tooltip bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn v-bind="attrs" v-on="on" icon fab>
            <v-icon v-clipboard:copy="text"> mdi-content-copy </v-icon>
          </v-btn>
        </template>
        <span>إضغط هنا للنسخ</span>
      </v-tooltip>
    </v-col>
  </v-row>

  <!-- <div cols="10" class="output ma-2">
    
    <div class="copy-btn">
      <v-tooltip bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn v-bind="attrs" v-on="on" icon fab>
            <v-icon v-clipboard:copy="text"> mdi-content-copy </v-icon>
          </v-btn>
        </template>
        <span>إضغط هنا للنسخ</span>
      </v-tooltip>
    </div>
  </div> -->
</template>

<script>
export default {
  props: {
    text: {
      default: "hi",
      type: String,
    },
    textAlign: {
      default: "text-center",
      type: String,
    },
  },
};
</script>
<style lang="scss">
// .output {
//   position: relative;
//   border-radius: 10px;

//   .copy-btn {
//     position: absolute;
//     left: 5px;
//     bottom: 5px;
//   }
// }
</style>
