<template>
  <!-- 顶部banner -->
  <div class="home-banner">
    <!-- 导航 -->
    <div class="home-banner-navigation">
      <div class="home-banner-navigation-left">Song</div>
      <div class="home-banner-navigation-right">
        <router-link to="/about">about</router-link>
        <router-link to="/blog">blog</router-link>
      </div>
    </div>

    <!-- 介绍 -->
    <div class="home-banner-desc">
      <div class="home-banner-desc-name">Song Blog</div>
      <div class="home-banner-desc-title">「 Eureka! 」</div>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {}
  },
  created() {},
  methods: {}
}
</script>

<style lang="scss">
.home-banner {
  // background: url('../../assets/image/bg-home-banner.jpg') no-repeat center 0;
  background-size: cover;

  &-navigation {
    height: 60px;
    font-size: 20px;
    font-weight: 800;
    display: flex;
    justify-content: space-between;
    align-items: center;

    &-left {
      padding-left: 20px;
    }

    &-right {
      padding-right: 20px;
    }
  }

  &-desc {
    font-weight: bold;

    &-name {
      font-size: 80px;
    }

    &-title {
      padding-top: 30px;
      font-size: 20px;
    }
  }
}
</style>
