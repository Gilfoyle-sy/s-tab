<template>
  <!-- 编辑框 -->
  <div class="bookmark-edit" v-show="showEdit" @click.self="close">
    <!-- 编辑框 -->
    <div class="bookmark-edit-box">
      <div class="bookmark-edit-box-row">
        <div class="bookmark-edit-name">网站名称</div>
        <input type="text" :value="newName" @input="onInputName" />
      </div>
      <div class="bookmark-edit-box-row">
        <div class="bookmark-edit-url">网站地址</div>
        <input type="text" :value="newUrl" @input="onInputUrl" />
      </div>

      <!-- 按钮 -->
      <div class="bookmark-edit-btn-confirm" @click="confirm">确定</div>
      <div class="bookmark-edit-btn-cancel" @click="close">取消</div>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  props: {
    showEdit: {
      type: Boolean,
      default: false
    },
    newName: {
      type: String,
      default: ''
    },
    newUrl: {
      type: String,
      default: ''
    }
  },
  methods: {
    // 关闭
    close() {
      this.$emit('close')
    },

    // 确认
    confirm() {
      this.$emit('confirm')
    },

    // 监听输入
    onInputName(e) {
      this.$emit('update:newName', e.target.value)
    },
    onInputUrl(e) {
      this.$emit('update:newUrl', e.target.value)
    }
  }
}
</script>

<style lang="scss">
// 编辑区域
.bookmark-edit {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 100;
  background: rgba($color: #000000, $alpha: 0.3);

  &-box {
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
    height: 200px;
    z-index: 110;
    background: red;
  }
}
</style>
