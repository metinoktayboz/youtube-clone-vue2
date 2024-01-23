<template>
  <div class="home">
    <v-toolbar class="sub-header pl-4" height="56" elevation="0">
      <v-btn
        v-for="(item, index) in subHeaderItems"
        :key="index"
        class="sub-header-btn"
        shaped
        small
      >
        {{ item.categoryName }}</v-btn
      >
    </v-toolbar>

    <div class="contents pt-6">
      <v-row
        v-for="(_rowNo, rowIndex) in getRowNumber"
        :key="rowIndex"
        class="mx-2"
        no-gutters
      >
        <template v-for="(item, index) in getVideoItemsPerRow(rowIndex)">
          <v-col
            :key="index"
            cols="12"
            sm="6"
            md="4"
            lg="3"
            xl=""
            class="px-2 pb-2"
          >
            <VideoCart
              :imgUrl="item.imgUrl"
              :avatarUrl="item.avatarUrl"
              :videoTitle="item.videoTitle"
              :channelName="item.channelName"
              :videoViews="item.videoViews"
              :time="item.time"
            ></VideoCart>
          </v-col>
        </template>
      </v-row>
    </div>
  </div>
</template>

<script>
import VideoCart from "../components/home/VideoCart.vue";

export default {
  name: "Home",
  components: {
    VideoCart,
  },
  data() {
    return {
      videoItems: [
        {
          imgUrl: "https://cdn.vuetifyjs.com/images/cards/cooking.png",
          avatarUrl:
            "https://avataaars.io/?avatarStyle=Transparent&topType=ShortHairShortCurly&accessoriesType=Prescription02&hairColor=Black&facialHairType=Blank&clotheType=Hoodie&clotheColor=White&eyeType=Default&eyebrowType=DefaultNatural&mouthType=Default&skinColor=Light",
          videoTitle: "Video Title - Video Title - Video Title -Video Title - ",
          channelName: "Channel 2",
          videoViews: "439 görüntülenme",
          time: "8 saat önce",
        },
        {
          imgUrl:
            "https://images.pexels.com/photos/320617/pexels-photo-320617.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
          avatarUrl:
            "https://avataaars.io/?avatarStyle=Circle&topType=ShortHairShaggyMullet&accessoriesType=Prescription01&hairColor=Blonde&facialHairType=BeardMajestic&facialHairColor=Platinum&clotheType=Hoodie&clotheColor=Blue03&graphicType=Pizza&eyeType=Surprised&eyebrowType=UpDown&mouthType=Eating&skinColor=Brown",
          videoTitle: "Video Title - Video Title - Video Title -Video Title",
          channelName: "Channel 3",
          videoViews: "789 görüntülenme",
          time: "2 saat önce",
        },
        {
          imgUrl:
            "https://images.pexels.com/photos/2541310/pexels-photo-2541310.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
          avatarUrl:
            "https://avataaars.io/?avatarStyle=Circle&topType=WinterHat3&accessoriesType=Wayfarers&hatColor=PastelYellow&hairColor=BlondeGolden&facialHairType=BeardLight&facialHairColor=Red&clotheType=GraphicShirt&clotheColor=White&graphicType=Selena&eyeType=Happy&eyebrowType=Default&mouthType=Tongue&skinColor=Tanned",
          videoTitle: "Video Title - Video Title - Video Title -Video Title",
          channelName: "Channel 4",
          videoViews: "789 görüntülenme",
          time: "2 saat önce",
        },
        {
          imgUrl:
            "https://images.pexels.com/photos/164879/pexels-photo-164879.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
          avatarUrl:
            "https://avataaars.io/?avatarStyle=Circle&topType=LongHairCurvy&accessoriesType=Prescription01&hairColor=Platinum&facialHairType=Blank&facialHairColor=Auburn&clotheType=CollarSweater&clotheColor=Black&eyeType=Dizzy&eyebrowType=RaisedExcitedNatural&mouthType=ScreamOpen&skinColor=Brown",
          videoTitle: "Video Title - Video Title - Video Title -Video Title",
          channelName: "Channel 5",
          videoViews: "789 görüntülenme",
          time: "2 saat önce",
        },
        {
          imgUrl:
            "https://images.pexels.com/photos/10326696/pexels-photo-10326696.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
          avatarUrl:
            "https://avataaars.io/?avatarStyle=Circle&topType=ShortHairTheCaesar&accessoriesType=Sunglasses&hairColor=Brown&facialHairType=MoustacheMagnum&facialHairColor=BlondeGolden&clotheType=Overall&clotheColor=Blue03&eyeType=EyeRoll&eyebrowType=UnibrowNatural&mouthType=Twinkle&skinColor=DarkBrown",
          videoTitle: "Video Title - Video Title - Video Title -Video Title",
          channelName: "Channel 6",
          videoViews: "789 görüntülenme",
          time: "2 saat önce",
        },
        {
          imgUrl:
            "https://images.pexels.com/photos/14086288/pexels-photo-14086288.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
          avatarUrl:
            "https://avataaars.io/?avatarStyle=Circle&topType=LongHairStraight&accessoriesType=Blank&hairColor=BlondeGolden&facialHairType=BeardMajestic&facialHairColor=Auburn&clotheType=GraphicShirt&clotheColor=Blue03&graphicType=Pizza&eyeType=Happy&eyebrowType=SadConcernedNatural&mouthType=Eating&skinColor=Black",
          videoTitle: "Video Title - Video Title - Video Title -Video Title",
          channelName: "Channel 7",
          videoViews: "789 görüntülenme",
          time: "2 saat önce",
        },
        {
          imgUrl:
            "https://images.pexels.com/photos/2156881/pexels-photo-2156881.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
          avatarUrl:
            "https://avataaars.io/?avatarStyle=Circle&topType=Hat&accessoriesType=Prescription01&facialHairType=Blank&clotheType=GraphicShirt&clotheColor=Gray01&graphicType=Skull&eyeType=EyeRoll&eyebrowType=RaisedExcited&mouthType=Grimace&skinColor=Pale",
          videoTitle: "Video Title - Video Title - Video Title -Video Title",
          channelName: "Channel 8",
          videoViews: "789 görüntülenme",
          time: "2 saat önce",
        },
        {
          imgUrl:
            "https://images.pexels.com/photos/5634861/pexels-photo-5634861.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
          avatarUrl:
            "https://avataaars.io/?avatarStyle=Circle&topType=LongHairMiaWallace&accessoriesType=Prescription01&hairColor=Blonde&facialHairType=BeardLight&facialHairColor=Platinum&clotheType=Hoodie&clotheColor=PastelRed&eyeType=Default&eyebrowType=Angry&mouthType=Sad&skinColor=Black",
          videoTitle: "Video Title - Video Title - Video Title -Video Title",
          channelName: "Channel 9",
          videoViews: "789 görüntülenme",
          time: "2 saat önce",
        },
        {
          imgUrl:
            "https://images.pexels.com/photos/370717/pexels-photo-370717.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
          avatarUrl:
            "https://avataaars.io/?avatarStyle=Circle&topType=LongHairStraightStrand&accessoriesType=Sunglasses&hatColor=PastelRed&hairColor=Blonde&facialHairType=MoustacheMagnum&facialHairColor=Platinum&clotheType=BlazerShirt&clotheColor=PastelGreen&eyeType=Hearts&eyebrowType=Angry&mouthType=Concerned&skinColor=Light",
          videoTitle: "Video Title - Video Title - Video Title -Video Title",
          channelName: "Channel 10",
          videoViews: "789 görüntülenme",
          time: "2 saat önce",
        },
        {
          imgUrl:
            "https://images.pexels.com/photos/5634860/pexels-photo-5634860.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
          avatarUrl:
            "https://avataaars.io/?avatarStyle=Circle&topType=WinterHat4&accessoriesType=Round&hatColor=Black&facialHairType=MoustacheFancy&facialHairColor=Black&clotheType=ShirtCrewNeck&clotheColor=Pink&graphicType=Selena&eyeType=Default&eyebrowType=RaisedExcited&mouthType=Sad&skinColor=Light",
          videoTitle: "Video Title - Video Title - Video Title -Video Title",
          channelName: "Channel 11",
          videoViews: "789 görüntülenme",
          time: "2 saat önce",
        },
        {
          imgUrl:
            "https://images.pexels.com/photos/3784143/pexels-photo-3784143.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
          avatarUrl:
            "https://avataaars.io/?avatarStyle=Circle&topType=WinterHat1&accessoriesType=Blank&hatColor=Red&hairColor=BlondeGolden&facialHairType=MoustacheMagnum&facialHairColor=BrownDark&clotheType=GraphicShirt&clotheColor=PastelOrange&graphicType=Bear&eyeType=Surprised&eyebrowType=RaisedExcited&mouthType=Grimace&skinColor=Black",
          videoTitle: "Video Title - Video Title - Video Title -Video Title",
          channelName: "Channel 1",
          videoViews: "789 görüntülenme",
          time: "2 saat önce",
        },
      ],
      subHeaderItems: [
        { categoryName: "Tümü" },
        { categoryName: "Category 1" },
        { categoryName: "Category 2" },
        { categoryName: "Category 3" },
        { categoryName: "Category 4" },
        { categoryName: "Category 5" },
        { categoryName: "Category 6" },
        { categoryName: "Category 7" },
        { categoryName: "Category 8" },
        { categoryName: "Category 9" },
      ],
      itemNumberPerRow: 5,
    };
  },
  computed: {
    getRowNumber() {
      return Math.ceil(this.videoItems.length / this.itemNumberPerRow);
    },
  },
  methods: {
    getVideoItemsPerRow(rowIndex) {
      const startIndex = rowIndex * this.itemNumberPerRow;

      return this.videoItems.slice(
        startIndex,
        startIndex + this.itemNumberPerRow
      );
    },
  },
};
</script>

<style lang="scss">
@import "@/assets/scss/views/home.scss";
</style>
