<template>
  <div id="about">
    <div class="container">
      <br>
      <h1 class="font-bold">About DadJokes</h1>

      <br>

      <h3>
        <i class="el-icon-info"></i>
        You can learn more about the website here
      </h3>

      <br><br>

      <p>This website is made with Nuxt.js, ElementUI and free dad jokes API</p>
      <br>
      <a href="https://icanhazdadjoke.com/api" target="_blank">Learn more about the API</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "about",
  head(){
      return {
          title: "About the DadJokes App",
          meta: [
              {
                  hid: "description",
                  name: "description",
                  content: "Best site for daily dose of corny dad jokes",
              }
          ]
      }
  }
}
</script>

<style>

</style>