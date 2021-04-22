<template>
  <div id="navbar">
    <el-menu :default-active="activeIndex" mode="horizontal">
        <el-container>
          <nuxt-link to="/" class="text-decoration-none"><el-menu-item index="1">Homepage</el-menu-item></nuxt-link>
          <nuxt-link to="/jokes" class="text-decoration-none"><el-menu-item index="2">Jokes</el-menu-item></nuxt-link>
          <nuxt-link to="/about" class="text-decoration-none"><el-menu-item index="3">About</el-menu-item></nuxt-link>
        </el-container>
    </el-menu>
  </div>
</template>

<script>
export default {
    data() {
      return {
        activeIndex: '1'
      };
    },
}
</script>

<style scoped>
.text-decoration-none {
  text-decoration: none !important;
}
</style>