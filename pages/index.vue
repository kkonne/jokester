<template>
  <div id="index">
    <div class="container">
      <br>
      <h1>DadJokes</h1>

      <br>

      <h3>🚀 Explore the magic of corny dad jokes</h3>

      <br><br>

      <p>Here's one random joke. Enjoy!</p>

      <div class="random-joke">
        <div v-if="joke">
          <nuxt-link :to="'/jokes/' + joke.id" class="nuxt-link">
            <div class="joke-card">
              <el-card shadow="always">
                {{ joke.joke }}
              </el-card>
            </div>
          </nuxt-link>
        </div>
        <div v-else v-loading="!joke" style="margin-top:70px">
        </div>
      </div>

      <nuxt-link to="/jokes">
        <el-button type="primary">See more jokes</el-button>
      </nuxt-link>
      <nuxt-link to="/about">
        <el-button type="primary" plain>About</el-button>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "index",

  data(){
    return {
      joke: undefined
    }
  },

  mounted(){
    const config = {
      headers: {
        'Accept': "application/json",
      },
    };

    fetch("https://icanhazdadjoke.com/", config)
    .then(response => response.json())
    .then(data => this.joke = data);
  },

  head(){
      return {
          title: "Dad Jokes | Homepage",
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
.container {
  width: 80%;
  margin: 0 auto;
  padding: 20px 0;
}

@media screen and (max-width: 768px) {
  .container {
    width: 95%;
  }
}

.nuxt-link {
  border: none !important;
  text-decoration: none !important;
}

.random-joke {
  margin: 20px 0;
}
</style>