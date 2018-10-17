<template>
  <!--TODO: Probably shouldn't be a hero-->
  <div class="hero" id="sample">
    <div class="hero-body">
      <a class="button primary" :class="{'is-loading': imageLoading}" @click="loadNewImage()">Generate a new sample!</a>
    </div>
    <div class="hero-body">
      <img class="sample-image" v-if="imageLoaded" :src="imageUrl" alt="Press the button for a wallpaper!">
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      urlCreator: window.URL || window.webkitURL,
      imageUrl: "",
      imageLoaded: false,
      imageLoading: false
    };
  },

  methods: {
    loadNewImage() {
      this.imageLoading = true;
      axios
        .post(
          "https://us-central1-wallpaper-bot.cloudfunctions.net/wallpaper-bot",
          { sample: true },
          { responseType: "blob" }
        )
        .then(response => {
          this.imageUrl = this.urlCreator.createObjectURL(response.data);
          this.imageLoaded = true;
          this.imageLoading = false;
        });
    }
  },

  created() {
    this.loadNewImage();
  }
};
</script>

<style>
.sample-image {
  width: 100%;
  max-width: 900px;
}
</style>
