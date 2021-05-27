<template>
  <v-slider
    v-model="zoom"
    append-icon="mdi-magnify-plus-outline"
    prepend-icon="mdi-magnify-minus-outline"
    @click:append="zoomIn"
    @click:prepend="zoomOut"
    @change="valueByEmit"
    min="250"
    max="500"
  ></v-slider>
</template>

<script>
export default {
  data() {
    return {
      zoom: 375
    };
  },
  methods: {
    zoomOut() {
      this.zoom = this.zoom - 10 || 0;
      this.$emit("slider-value", this.zoom);
    },
    zoomIn() {
      this.zoom = this.zoom + 10 || 100;
      this.$emit("slider-value", this.zoom);
    },
    valueByEmit() {
      this.$emit("slider-value", this.zoom);
    }
  }
};
</script>

<style></style>
