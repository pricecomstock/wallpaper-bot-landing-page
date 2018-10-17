<template>
  <div class="home">
    <slack-button/>
    <sample></sample>
  </div>
</template>

<script>
// @ is an alias to /src
import SlackButton from "@/components/SlackButton.vue";
import Sample from "@/components/Sample.vue";

export default {
  name: "home",
  components: {
    SlackButton,
    Sample
  }
};
</script>
