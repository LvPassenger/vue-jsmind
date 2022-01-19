<template>
  <div id="app">
    <!-- <Demo></Demo> -->
    <JsMind></JsMind>
  </div>
</template>

<script>
import JsMind from './components/Jsmind.vue'
// import Demo from './components/Demo.vue'

export default {
  name: 'App',
  components: {
    // Demo,
    JsMind
  }
}
</script>

<style lang="less">
@import "assets/css/reset.less";
</style>
