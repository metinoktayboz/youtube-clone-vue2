<template>
  <div>
    <v-app-bar app elevation="0" dark height="56" clipped-left>
      <div class="header">
        <v-col class="left-header">
          <v-app-bar-nav-icon @click="mini = !mini"></v-app-bar-nav-icon>

          <v-toolbar-title>
            <router-link to="/" tag="span" style="cursor: pointer"
              >YouTube</router-link
            >
          </v-toolbar-title>
        </v-col>
        <v-col class="mid-header">
          <v-text-field
            class="search-bar"
            placeholder="Ara"
            color="blue darken-3"
            outlined
            dense
            clearable
            hide-details
          ></v-text-field>

          <span class="search-icon mdi mdi-magnify"></span>

          <v-btn class="microphone-icon" icon>
            <v-icon class="mdi mdi-microphone"></v-icon>
          </v-btn>
        </v-col>

        <v-col class="right-header">
          <v-btn class="video-icon" icon>
            <v-icon class="mdi mdi-video-plus-outline"></v-icon>
          </v-btn>

          <v-btn class="bell-icon" icon>
            <v-icon class="mdi mdi-bell-outline"></v-icon>
          </v-btn>

          <div class="profile-icon" icon>
            <v-icon class="profile-photo"></v-icon>
          </div>
        </v-col>
      </div>
    </v-app-bar>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant.sync="mini"
      class="no-transition"
      permanent
      clipped
      dark
      app
      mini-variant-width="72"
      width="240"
      floating
    >
      <v-list v-if="mini" class="mini-list">
        <v-list-item v-for="item in itemsClosed" :key="item.title" link>
          <v-list-item-content>
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <span class="item-title text-no-wrap">{{ item.title }}</span>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <v-list v-else class="open-list" dense rounded>
        <v-list-item
          class="drawer-list-item"
          v-for="item in itemsOpen"
          :key="item.title"
          link
        >
          <v-list-item-content>
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <span class="item-title-large">{{ item.title }}</span>
          </v-list-item-content>
        </v-list-item>

        <v-divider class="mt-3 pt-3"></v-divider>

        <v-list-item class="drawer-list-item" link>
          <v-list-item-content>
            <span class="title-siz pr-2"> Siz </span>
            <v-list-item-icon>
              <v-icon class="chevron-right">mdi-chevron-right</v-icon>
            </v-list-item-icon>
          </v-list-item-content>
        </v-list-item>

        <v-list-item
          class="drawer-list-item"
          v-for="item in shownItems"
          :key="item.title"
          link
        >
          <v-list-item-content>
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <span class="item-title-large">{{ item.title }}</span>
          </v-list-item-content>
        </v-list-item>

        <v-list-item
          class="drawer-list-item"
          @click="expandOrCollapseYouItems"
          link
        >
          <v-list-item-content v-if="!isExpanded">
            <v-list-item-icon>
              <v-icon>mdi-chevron-down</v-icon>
            </v-list-item-icon>
            <span class="item-title-large">Daha fazla göster</span>
          </v-list-item-content>
          <v-list-item-content v-if="isExpanded">
            <v-list-item-icon>
              <v-icon>mdi-chevron-up</v-icon>
            </v-list-item-icon>
            <span class="item-title-large">Daha az göster</span>
          </v-list-item-content>
        </v-list-item>

        <v-divider class="mt-3 pt-3"></v-divider>

        <v-list-item class="subs-title">
          <v-list-item-content class="subs">
            <span class="title-siz"> Abonelikler </span>
          </v-list-item-content>
        </v-list-item>

        <v-list-item
          class="drawer-list-item"
          v-for="item in subs"
          :key="item.title"
          link
        >
          <v-list-item-content>
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <span class="item-title-large">{{ item.title }}</span>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  name: "Header",

  data() {
    return {
      drawer: true,
      mini: false,
      isExpanded: true,
      dynamicWidth: window.innerWidth,
      itemsClosed: [
        { title: "Ana Sayfa", icon: "mdi-home-variant" },
        { title: "Shorts", icon: "mdi-youtube-tv" },
        { title: "Abonelikler", icon: "mdi-youtube-subscription" },
        { title: "Youtube Music", icon: "mdi-cast-audio-variant" },
        { title: "Siz", icon: "mdi-play-box-multiple-outline" },
        { title: "İndirilenler", icon: "mdi-download" },
      ],
      itemsOpen: [
        { title: "Ana Sayfa", icon: "mdi-home-variant" },
        { title: "Shorts", icon: "mdi-youtube-tv" },
        { title: "Abonelikler", icon: "mdi-youtube-subscription" },
        { title: "Youtube Music", icon: "mdi-cast-audio-variant" },
      ],
      itemsYou: [
        { title: "Kanalınız", icon: "mdi-account-box-outline" },
        { title: "Geçmiş", icon: "mdi-history" },
        { title: "Videolarınız", icon: "mdi-play-box-outline" },
        { title: "Daha sonra izle", icon: "mdi-clock-time-five-outline" },
        { title: "İndirilenler", icon: "mdi-download" },
      ],
      itemsYouExpanded: [
        { title: "Kanalınız", icon: "mdi-account-box-outline" },
        { title: "Geçmiş", icon: "mdi-history" },
        { title: "Videolarınız", icon: "mdi-play-box-outline" },
        { title: "Daha sonra izle", icon: "mdi-clock-time-five-outline" },
        { title: "İndirilenler", icon: "mdi-download" },
        { title: "Beğendiğim videolar", icon: "mdi-thumb-up-outline" },
        { title: "playlist", icon: "mdi-playlist-play" },
      ],
      shownItems: [],
      subs: [
        { title: "Abonelik 1", icon: "mdi-face-man-profile" },
        { title: "Abonelik 2", icon: "mdi-face-man-profile" },
        { title: "Abonelik 3", icon: "mdi-face-man-profile" },
        { title: "Abonelik 4", icon: "mdi-face-man-profile" },
        { title: "Abonelik 5", icon: "mdi-face-man-profile" },
      ],
    };
  },
  methods: {
    expandOrCollapseYouItems() {
      this.shownItems = this.isExpanded
        ? this.itemsYou.map((item) => ({ ...item }))
        : this.itemsYouExpanded.map((item) => ({ ...item }));
      this.isExpanded = !this.isExpanded;
    },
  },
  created() {
    this.expandOrCollapseYouItems();
    window.onresize = () => {
      this.dynamicWidth = window.innerWidth;
    };
  },

  watch: {
    dynamicWidth() {
      if (this.dynamicWidth < 1313) {
        this.mini = true;
      }
    },
  },
};
</script>

<style lang="scss">
@import "@/assets/scss/components/header.scss";
</style>
