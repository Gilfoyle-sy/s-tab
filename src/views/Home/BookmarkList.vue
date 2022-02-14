<template>
  <!-- 书签列表 -->
  <div class="bookmark-list">
    <div
      class="bookmark-list-item"
      v-for="(item, index) in list"
      :key="item.timestamp"
      @contextmenu.prevent="ready({ item, index })"
    >
      <!-- 网站图片 -->
      <div :class="[{ animate: showMask }, 'bookmark-list-item-img']">
        <div>{{ item.name.substr(0, 1) }}</div>
        <!-- <div v-if="item.imgUrl.length === 0">{{ item.name.substr(0, 1) }}</div>
        <img v-else :src="item.imgUrl" alt="" /> -->
      </div>

      <!-- 网站名称 -->
      <div class="bookmark-list-item-name">{{ item.name }}</div>

      <!-- 编辑时蒙层 -->
      <div :class="[{ animate: showMask }, 'bookmark-list-item-btn']" v-if="showMask">
        <div class="bookmark-list-item-btn-del" @click="del(index)">
          <i class="iconfont">&#xe690;</i>
        </div>
        <div class="bookmark-list-item-btn-edit" @click="edit({ item, index })">
          <i class="iconfont">&#xe600;</i>
        </div>
      </div>
    </div>

    <div class="bookmark-list-mask" v-if="showMask" @click="showMask = false"></div>
  </div>
</template>

<script>
export default {
  components: {},
  props: {
    list: {
      type: Array,
      default: () => {
        return []
      }
    }
  },
  data() {
    return {
      showMask: false
    }
  },

  methods: {
    // 编辑
    edit(val) {
      this.showMask = false
      this.$emit('edit', val)
    },

    // 删除
    del(index) {
      this.$emit('del', index)
    },

    // 右键
    ready() {
      this.showMask = true
    }
  }
}
</script>

<style lang="scss">
.bookmark-list {
  display: flex;
  flex-wrap: wrap;
  max-width: 100%;

  &-mask {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 100;
  }

  &-item {
    position: relative;
    display: flex;
    flex-flow: column;
    margin: 15px 30px 0 30px;

    .animate {
      animation-name: shaking;
      animation-duration: 0.3s;
      animation-timing-function: ease;
      animation-iteration-count: infinite;
    }

    &-img {
      width: 60px;
      height: 60px;
      border-radius: 10px;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    &-name {
      padding-top: 10px;
    }

    &-btn {
      position: absolute;
      z-index: 110;
      top: 0;
      left: 0;
      width: 60px;
      height: 60px;
      border: 1px solid black;
      border-radius: 10px;
      background: rgba($color: #ffffff, $alpha: 0.8);

      &-del {
        position: absolute;
        top: -8px;
        right: -8px;

        .iconfont {
          font-size: 18px;
          opacity: 0.5;
        }
      }

      &-edit {
        position: absolute;
        bottom: -8px;
        right: -8px;

        .iconfont {
          font-size: 20px;
          opacity: 0.5;
        }
      }
    }
  }
}

@keyframes shaking {
  25% {
    transform: rotate(2deg);
  }

  50% {
    transform: rotate(0deg);
  }

  75% {
    transform: rotate(-2deg);
  }

  100% {
    transform: rotate(0deg);
  }
}
</style>
