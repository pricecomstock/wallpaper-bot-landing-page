<template>
  <div class="thanks">
    <p>Thanks for adding Inspo-paper to Slack!</p>
    <p>Give it a try by clicking the <button class="button is-small"><span class="icon is-small"><i class="fas fa-ellipsis-h"></i></span></button> next to a slack message!</p>
  </div>
</template>

<script>
export default {
  name: "home",
  data() {
    return {
      oauthUrl:
        "https://us-central1-wallpaper-bot.cloudfunctions.net/wallpaper-oauth"
    };
  }
};
</script>
