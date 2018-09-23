<template>
  <div class="home">
    <slack-button msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import SlackButton from "@/components/SlackButton.vue";

export default {
  name: "home",
  components: {
    SlackButton
  }
};
</script>
