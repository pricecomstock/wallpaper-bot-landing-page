<template>
  <div>
    <div class="hero">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">
            Inspo-paper
          </h1>
          <h2 class="subtitle">
            immortalize messages as beautiful and inspirational images!
          </h2>
        </div>
      </div>
    </div>
    <div class="hero">
      <div class="hero-body">
        <a href="https://slack.com/oauth/authorize?client_id=400168532339.400446261685&scope=commands,users:read"><img alt="Add to Slack" height="40" width="139" src="https://platform.slack-edge.com/img/add_to_slack.png" srcset="https://platform.slack-edge.com/img/add_to_slack.png 1x, https://platform.slack-edge.com/img/add_to_slack@2x.png 2x" /></a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SlackButton",
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
