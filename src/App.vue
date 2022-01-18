<template>
  <div id="app">
    <JsMind></JsMind>
  </div>
</template>

<script>
import JsMind from './components/Jsmind.vue'

export default {
  name: 'App',
  components: {
    JsMind
  }
}
</script>

<style lang="less">
@import "assets/css/reset.less";
</style>
