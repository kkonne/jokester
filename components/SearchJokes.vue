<template>
  <div id="search-jokes">
    <form @submit.prevent="onSearch">
        <el-input
            placeholder="Search jokes"
            prefix-icon="el-icon-search"
            v-model="searchInput">
        </el-input>
    </form>

  </div>
</template>

<script>
export default {
    name: "SearchJokes",

    data(){
        return {
            searchInput: undefined,
        }
    },

    methods: {
        onSearch() {
            if(!this.searchInput){
                this.$message.error('An error occurred: Invalid input!');
                return;
            }

            this.$emit("search-input", this.searchInput);
            this.searchInput = "";
        }
    }
}
</script>

<style scoped>
#search-jokes {
    margin: 20px 0;
}
</style>