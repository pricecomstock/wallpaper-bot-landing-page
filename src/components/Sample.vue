<template>
  <!--TODO: Probably shouldn't be a hero-->
  <div class="hero" id="sample">
    <div class="container">
      <hr>
      <div class="section">
        <div>
          <img src="@/assets/messagebutton.png" alt="Message Action">
        </div>
        Just click the <button class="button is-small"><span class="icon is-small"><i class="fas fa-ellipsis-h"></i></span></button> on the Slack message you want to create a wallpaper from!
      </div>
      <hr>
      <div class="section">
        <div class="field">
          <p class="control has-text-centered">
            <a class="button is-danger is-large" :class="{'is-loading': imageLoading}" @click="loadNewImage()">Generate a new sample!</a>
          </p>
        </div>
        <p class="is-size-6">These quotes and wallpapers are chosen randomly and do not reflect the views of Inspopaper!</p>
      </div>
      <div class="section">
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
