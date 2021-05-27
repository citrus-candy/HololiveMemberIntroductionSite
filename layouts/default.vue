<template>
  <v-app>
    <v-main>
      <v-container>
        <Tabs />
        <Slider @slider-value="emitEvent" />
        <nuxt />
        <v-tabs center-active v-model="tab">
          <v-tab href="#all">All</v-tab>
          <v-tab href="#gen0">0期生</v-tab>
          <v-tab href="#gen1">1期生</v-tab>
          <v-tab href="#gen2">2期生</v-tab>
          <v-tab href="#gamers">ゲーマーズ</v-tab>
          <v-tab href="#gen3">3期生</v-tab>
          <v-tab href="#gen4">4期生</v-tab>
          <v-tab href="#gen5">5期生</v-tab>
        </v-tabs>
        <v-tabs-items class="card" v-model="tab" v-show="tab == 'all'">
          <Card
            v-for="(text, key) in texts"
            :key="key"
            :name="text.name"
            :image_link="text.image_link"
            :description="text.description"
            :youtube_link="text.youtube_link"
            :twitter_link="text.twitter_link"
            grade="all"
            :slider_value="slider()"
          />
        </v-tabs-items>
        <v-tabs-items class="card" v-model="tab" v-show="tab != 'all'">
          <Card
            v-for="(text, key) in texts"
            :key="key"
            :name="text.name"
            :image_link="text.image_link"
            :description="text.description"
            :youtube_link="text.youtube_link"
            :twitter_link="text.twitter_link"
            :grade="text.grade"
            :slider_value="slider()"
          />
        </v-tabs-items>
      </v-container>
    </v-main>
    <v-navigation-drawer v-model="rightDrawer" :right="right" temporary fixed>
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light>
              mdi-repeat
            </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-footer :absolute="!fixed" app> </v-footer>
  </v-app>
</template>

<script>
import text_json from "../static/text";

export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: "mdi-apps",
          title: "Welcome",
          to: "/"
        },
        {
          icon: "mdi-chart-bubble",
          title: "Inspire",
          to: "/inspire"
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "Vuetify.js",
      sliderValue: 375,
      texts: text_json,
      tab: "",
      all: "all"
    };
  },
  methods: {
    emitEvent(sliderValue) {
      this.sliderValue = sliderValue;
    },
    slider() {
      return this.sliderValue;
    }
  }
};
</script>

<style scoped>
.v-window >>> div.v-window__container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  min-height: 100vh;
}
</style>
