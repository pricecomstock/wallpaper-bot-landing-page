<template>
  <!--TODO: Probably shouldn't be a hero-->
  <div class="hero" id="sample">
    <div class="section">
      <div class="field">
        <p class="control has-text-centered">
          <a class="button primary is-large" :class="{'is-loading': imageLoading}" @click="loadNewImage()">Generate a new sample!</a>
        </p>
      </div>
      <p class="is-size-6">These quotes are chosen randomly from over 36,000 quotes and do not reflect the views of Inspopaper!</p>
      <hr>
      <div class="container">
        <img class="sample-image" v-if="imageLoaded" :src="imageUrl" alt="Press the button for a wallpaper!">
      </div>
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
