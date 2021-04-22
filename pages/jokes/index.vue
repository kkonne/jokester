<template>
  <div id="jokes">
      <div class="container">
        <br>
        <h1>Explore dad jokes</h1>
        <br>
        <h3>
          <i class="el-icon-share"></i>
          Share the best jokes with your friends</h3>
        
        <SearchJokes v-on:search-input="searchText" />

        <div v-for="joke in jokes" :key="joke.id">
          <nuxt-link :to="'/jokes/' + joke.id" class="nuxt-link">
            <div class="joke-card">
              <el-card shadow="always">
                {{ joke.joke }}
              </el-card>
            </div>
          </nuxt-link>
          <br>
        </div>
        <el-button v-if="searchActive" @click="searchAll" type="primary" plain>Show all jokes</el-button>

        <div class="paginate-buttons" v-if="!searchActive">
          <el-button v-if="jokes" @click="previousPage" :plain="(paginate.current_page === paginate.previous_page)" type="primary" :disabled="(paginate.current_page === paginate.previous_page)">Previous page</el-button>
          <el-button v-if="jokes" @click="nextPage" :plain="(paginate.current_page === paginate.next_page)" type="primary" :disabled="(paginate.current_page === paginate.next_page)">Next page</el-button>
        </div>

      </div>
  </div>
</template>

<script>
import SearchJokes from "../../components/SearchJokes";

export default {
    name: "jokes",

    components: {
      SearchJokes,
    },

    data(){
      return {
        jokes: undefined,
        paginate: undefined,
        searchActive: false,
      }
    },

    methods: {
      previousPage(){
        const config = {
          headers: {
            'Accept': "application/json",
          },
        };

        fetch("https://icanhazdadjoke.com/search?page="+this.paginate.previous_page, config)
        .then(response => response.json())
        .then(data => {
          this.jokes = data.results;
          this.paginate = data;
        });
      },

      nextPage(){
        const config = {
          headers: {
            'Accept': "application/json",
          },
        };

        fetch("https://icanhazdadjoke.com/search?page="+this.paginate.next_page, config)
        .then(response => response.json())
        .then(data => {
          this.jokes = data.results;
          this.paginate = data;
        });
      },

      searchText(text){
        const config = {
          headers: {
            'Accept': "application/json",
          },
        };

        fetch("https://icanhazdadjoke.com/search?term=" + text, config)
        .then(response => response.json())
        .then(data => this.jokes = data.results);

        this.searchActive = true;
      },

      searchAll(){
        const config = {
          headers: {
            'Accept': "application/json",
          },
        };

        fetch("https://icanhazdadjoke.com/search", config)
        .then(response => response.json())
        .then(data => {
          this.jokes = data.results;
          this.paginate = data;
        });

        this.searchActive = false;
      }
    },

    created(){
      this.searchAll();
    },

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

<style scoped>
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

.paginate-buttons {
  display: flex;
  align-content: center;
  justify-content: center;
}
</style>