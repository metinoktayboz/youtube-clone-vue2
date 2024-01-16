<template>
  <div class="video-cart pa-0">
    <v-card elevation="0">
      <v-img height="60%" :src="imgUrl"></v-img>
      <v-list-item>
        <v-list-item-avatar height="36" min-width="36" width="36">
          <v-img class="elevation-6" alt="" :src="avatarUrl"></v-img>
        </v-list-item-avatar>

        <v-list-item-content class="pr-md-2 py-0">
          <h3 class="video-title">
            <a href="#">
              {{ videoTitle }}
            </a>
          </h3>
          <div class="sub-text">
            <div class="channel-name">
              <a href="#">{{ channelName }}</a>
            </div>
            <div class="video-info">
              <span>{{ videoViews }}</span>
              <span class="time-info">{{ time }}</span>
            </div>
          </div>
        </v-list-item-content>
      </v-list-item>
    </v-card>
  </div>
</template>

<script>
export default {
  name: "VideoCart",
  props: {
    imgUrl: { type: String },
    avatarUrl: { type: String },
    videoTitle: { type: String },
    channelName: { type: String },
    videoViews: { type: String },
    time: { type: String },
  },
};
</script>

<style lang="scss">
@import "@/assets/scss/components/home/videoCart.scss";
</style>
