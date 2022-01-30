<template>
  <router-view/>
</template>

<script>
  import Home from "@/views/Home.vue";
  export default{
    components: {
      // Home
    }
  }
</script>

<style lang="scss" >


$font-array: -apple-system, BlinkMacSystemFont, "San Francisco", "Helvetica Neue", Helvetica, Ubuntu, Roboto, Noto, "Segoe UI", Arial, sans-serif;
  
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body{
    margin: var(--base-margin-xyA);
  }
#app {
  font-family: $font-array;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  // color: #2c3e50;
}


</style>
