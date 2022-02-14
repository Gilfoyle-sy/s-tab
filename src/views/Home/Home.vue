<template>
  <div class="home">
    <!-- 顶部展示区 -->
    <Banner></Banner>

    <!-- 书签区域 -->
    <Bookmark></Bookmark>

    <!-- 底部栏 -->
    <FooterBar></FooterBar>

    <!-- <div v-for="(item, index) in arr" :key="item.name">
      name:{{ item.name }},age:{{ item.age }},index:{{ index }}__
      <span @click="add">加</span>
      <span @click="del(index)">删</span>
      <span @click="change(index)">改</span>
    </div> -->
  </div>
</template>

<script>
import Banner from './Banner.vue'
import Bookmark from './Bookmark.vue'
import FooterBar from '../../components/FooterBar.vue'

export default {
  components: {
    Banner,
    Bookmark,
    FooterBar
  },
  data() {
    return {
      arr: [
        {
          name: 1,
          age: 1
        },
        {
          name: 2,
          age: 2
        },
        {
          name: 3,
          age: 3
        }
      ]
    }
  },
  methods: {
    // add() {
    //   this.arr.push({ name: 2, age: 2 })
    // },
    // del(index) {
    //   this.arr.splice(index, 1)
    // },
    // change(index) {
    //   console.log(this.arr[index])
    //   // this.arr[index] = { ...{ name: 2, age: 2 } }
    //   this.$set(this.arr[index], 'name', 2)
    //   this.$set(this.arr[index], 'age', 2)
    //   console.log(this.arr)
    // }
  }
}
</script>

<style lang="scss">
.home {
}
</style>
