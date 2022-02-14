<template>
  <div class="blog">
    <!-- 顶部菜单 -->
    <div class="blog-header">顶部菜单栏</div>

    <!-- 中部内容 -->
    <div class="blog-content">
      <!-- 左侧菜单 -->
      <div class="blog-content-sider">左侧列表</div>
      <!-- 右侧内容 -->
      <div class="blog-content-article">
        <Editor
          :value="value"
          :plugins="plugins"
          @change="handleChange"
          :locale="zhHans"
        />
        <!-- <Viewer :plugins="plugins" :locale="zhHans"></Viewer> -->
      </div>
    </div>

    <!-- 底部状态 -->
    <div class="blog-footer">底部区域</div>
  </div>
</template>

<script>
import { Editor } from '@bytemd/vue'
// import gfm from '@bytemd/plugin-gfm'
import zhHans from 'bytemd/lib/locales/zh_Hans.json'
import 'bytemd/dist/index.min.css'

const plugins = [
  // gfm()
  // Add more plugins here
]

export default {
  components: { Editor },
  data() {
    return { value: '', plugins, zhHans }
  },
  methods: {
    handleChange(v) {
      this.value = v
      console.log(this.value)
    }
  }
}
</script>

<style lang="scss">
.blog {
  width: 100%;
  height: 100%;
  display: flex;
  flex-flow: column;

  &-header {
    height: 60px;
    background: red;
  }

  &-content {
    flex: 1;
    display: flex;

    &-sider {
      width: 300px;
      border-right: 1px solid black;
    }

    &-article {
      flex: 1;

      .bytemd {
        height: calc(100vh - 85px);
      }
    }
  }

  &-footer {
    height: 25px;
    background: red;
  }
}
</style>
