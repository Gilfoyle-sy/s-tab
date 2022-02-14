<template>
  <div class="bookmark-search">
    <!-- 类型 -->
    <div class="bookmark-search-type">
      <i class="iconfont">&#xe8cb;</i>
    </div>

    <!-- 输入框 -->
    <div class="bookmark-search-input">
      <input type="text" placeholder="输入并搜索" v-model="searchVal" @keyup.enter="search" />
    </div>

    <!-- 按钮 -->
    <div class="bookmark-search-btn" @click="search">
      <i class="iconfont">&#xe66a;</i>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      searchVal: ''
    }
  },
  created() {},
  methods: {
    search() {
      const url = `https:///www.baidu.com/s?wd=${this.searchVal}`
      window.open(url)
    }
  }
}
</script>

<style lang="scss">
.bookmark-search {
  margin: 0 auto;
  padding: 30px 0;
  display: flex;
  justify-content: center;
  align-items: center;

  &-type {
    width: 50px;
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid #42b983;
    border-top-left-radius: 10px;
    border-bottom-left-radius: 10px;
    border-right: none;

    .iconfont {
      color: #3244df;
      font-size: 25px;
    }
  }
  &-input {
    width: 460px;
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid #42b983;
    border-left: none;
    border-right: none;
    input {
      width: 100%;
      height: 50px;
      padding: 0 10px;
      border: 0;
      outline: none;
      font-size: 16px;
      line-height: normal;
      &::placeholder {
        transform: translateY(1px);
      }
    }
    input::-webkit-input-placeholder {
      /* WebKit browsers */
      color: #999999;
    }
    input:-moz-placeholder {
      /* Mozilla Firefox 4 to 18 */
      color: #999999;
    }
    input::-moz-placeholder {
      /* Mozilla Firefox 19+ */
      color: #999999;
    }
    input:-ms-input-placeholder {
      /* Internet Explorer 10+ */
      color: #999999;
    }
  }

  &-btn {
    width: 50px;
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid #42b983;
    border-top-right-radius: 10px;
    border-bottom-right-radius: 10px;
    border-left: none;
    background: #42b983;

    .iconfont {
      font-size: 20px;
      color: #ffffff;
    }
  }
}
</style>
