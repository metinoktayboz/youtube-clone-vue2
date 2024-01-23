<template>
  <v-app>
    <Header></Header>
    <v-main>
      <router-view />
      <v-bottom-navigation
        class="align-center justify-space-around hidden-sm-and-up"
        background-color="#0f0f0f"
        fixed
      >
        <v-btn
          color="rgb(15, 15, 15)"
          v-for="(item, index) in bottomNavItems"
          :key="index"
        >
          <span>{{ item.title }}</span>

          <v-icon>{{ item.icon }}</v-icon>
        </v-btn>
      </v-bottom-navigation>
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
    bottomNavItems: [
      { title: "Ana Sayfa", icon: "mdi-home-variant" },
      { title: "Shorts", icon: "mdi-youtube-tv" },
      { title: "Abonelikler", icon: "mdi-youtube-subscription" },
      { title: "Youtube Music", icon: "mdi-cast-audio-variant" },
    ],
  }),
};
</script>
<style lang="scss">
@import "@/assets/scss/app.scss";
</style>
