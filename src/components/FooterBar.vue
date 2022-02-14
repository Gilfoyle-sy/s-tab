<template>
  <div class="footer-bar">
    底部栏目
    <div class="footer-bar-item footer-bar-location">位置</div>
    <div class="footer-bar-item footer-bar-weather">天气</div>
    <div class="footer-bar-item footer-bar-version">版本</div>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {}
  },
  created() {}
}
</script>

<style lang="scss">
.footer-bar {
  position: fixed;
  bottom: 0;
  width: 100%;
  height: 30px;
  background: #1b1e2c;
  color: aliceblue;

  display: flex;
  justify-content: space-between;

  &-item {
  }
}
</style>
