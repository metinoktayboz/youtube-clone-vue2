<template>
  <v-app>
    <Header></Header>
    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
import Header from "./components/Header";

export default {
  name: "App",
  components: {
    Header,
  },

  data: () => ({
    //
  }),
};
</script>
<style lang="scss">
@import "@/assets/scss/app.scss";
</style>
