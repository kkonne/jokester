<template>
  <div id="joke-id">
      <div class="container">
        <div class="back-button">
          <nuxt-link to="/jokes" class="text-decoration-none">
              <i class="el-icon-arrow-left"></i>
              Back to jokes
          </nuxt-link>
        </div>
        
        

        <div class="joke-card">
          <el-card shadow="always">
            <div class="text-muted">id: #{{ $route.params.id }}</div>
            <h2 class="joke">{{ joke }}</h2>
          </el-card>
        </div>
        
        <br>
        <div>
          Share with friends:
          <el-tooltip class="item" effect="dark" content="Copy to clipboard" placement="top-start">
          <el-button @click="copyToClipboard">
            {{ shareLink }} 
            <i class="el-icon-document-copy"></i>
          </el-button>
        </el-tooltip>
        </div>
        

      </div>
  </div>
</template>

<script>
export default {
    name: "joke",

    data(){
      return {
        joke: undefined,
        shareLink: "https://www.dadjokes.com" + this.$route.fullPath
      }
    },

    methods: {
      copyToClipboard(){
        /* Get the text field */
        let copyText = this.shareLink;

        navigator.clipboard.writeText(copyText);

        this.$message({
          showClose: true,
          message: 'Copied to clipboard',
          type: 'success'
        });
      }
    },

    created(){
      const config = {
        headers: {
          'Accept': "application/json",
        },
      };

      fetch("https://icanhazdadjoke.com/j/" + this.$route.params.id, config)
      .then(response => response.json())
      .then(data => this.joke = data.joke);
    },
}
</script>

<style scoped>
.text-muted {
  color: #999999;
  font-size: .7rem;
  text-transform: uppercase;
}

.joke {
  margin: 15px 0;
}

.back-button {
  margin: 20px 0;
}

.text-decoration-none {
  text-decoration: none;
  color: #202020;
}
</style>