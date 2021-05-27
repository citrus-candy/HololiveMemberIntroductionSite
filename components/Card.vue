<template>
  <v-tab-item :value="_grade">
    <v-card class="mx-auto my-12" :max-width="slider" elevation="6">
      <v-img height="250" :src="image_URL"></v-img>
      <v-card-title>{{ name }}</v-card-title>
      <v-card-actions>
        <v-btn text>
          詳細
        </v-btn>
        <v-spacer></v-spacer>
        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? "mdi-chevron-up" : "mdi-chevron-down" }}</v-icon>
        </v-btn>
      </v-card-actions>
      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>
          <v-card-text>
            <div v-html="description"></div>
          </v-card-text>
        </div>
      </v-expand-transition>
      <v-divider class="mx-4"></v-divider>
      <v-card-actions>
        <v-btn color="red darken-2" text target="_blank" :href="youtube_URL">
          <v-icon>mdi-youtube</v-icon>
          Youtube
        </v-btn>
        <v-btn
          color="light-blue lighten-1"
          text
          target="_blank"
          :href="twitter_URL"
        >
          <v-icon>mdi-twitter</v-icon>
          Twitter
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-tab-item>
</template>

<script>
export default {
  props: [
    "name",
    "image_link",
    "description",
    "youtube_link",
    "twitter_link",
    "slider_value",
    "grade"
  ],
  computed: {
    image_URL: function() {
      return this.image_link;
    },
    youtube_URL: function() {
      return this.youtube_link;
    },
    twitter_URL: function() {
      return this.twitter_link;
    },
    slider: function() {
      return this.slider_value;
    },
    _grade: function() {
      return this.grade;
    }
  },
  data() {
    return {
      show: false,
      show2: false
    };
  },
  methods: {
    show_card() {
      if (this.grade == "gen0") {
        return true;
      } else {
        return false;
      }
    }
  }
};
</script>

<style scoped>
.v-image {
  background-color: white;
}
</style>
