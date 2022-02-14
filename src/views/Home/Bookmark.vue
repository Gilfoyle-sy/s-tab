<template>
  <div class="bookmark">
    <!-- 搜索框 -->
    <BookmarkSearch></BookmarkSearch>

    <!-- 列表 -->
    <BookmarkList :list="list" @edit="edit"></BookmarkList>

    <!-- 编辑框 -->
    <BookmarkEdit
      :showEdit="showEdit"
      :newName.sync="newName"
      :newUrl.sync="newUrl"
      @close="close"
      @confirm="confirm"
    ></BookmarkEdit>

    <div @click="add">添加</div>
  </div>
</template>

<script>
import BookmarkSearch from './BookmarkSearch.vue'
import BookmarkList from './BookmarkList.vue'
import BookmarkEdit from './BookmarkEdit.vue'

export default {
  components: {
    BookmarkSearch,
    BookmarkList,
    BookmarkEdit
  },
  data() {
    return {
      showEdit: false, // 显示编辑框
      isAdd: false, // 是否是新增
      editIndex: 0, // 正在编辑的index
      newName: '', // 编辑框内名字
      newUrl: '', // 编辑框内url
      list: [
        {
          name: '百度',
          url: 'www.baidu.com',
          timestamp: 1643693111022
        },
        {
          name: '网易',
          url: 'www.163.com',
          timestamp: 164369321022
        }
      ]
    }
  },
  methods: {
    // reset数据
    resetEditInfo() {
      this.isAdd = false
      this.editIndex = 0
      this.newName = ''
      this.newUrl = ''
      this.showEdit = false
    },

    // 添加
    add(item) {
      this.showEdit = true
      this.isAdd = true
    },

    // 关闭
    close() {
      this.resetEditInfo()
    },

    // 确认
    confirm() {
      if (this.isAdd) {
        // 新增
        this.list = [
          ...this.list,
          { name: this.newName, url: this.newUrl, timestamp: new Date().getTime() }
        ]
      } else {
        // 编辑
        this.list[this.editIndex].name = this.newName
        this.list[this.editIndex].url = this.newUrl
        this.list[this.editIndex].timestamp = new Date().getTime()
      }

      console.log(this.list)

      this.resetEditInfo()
    },

    // 编辑
    edit(val) {
      this.showEdit = true
      this.newName = val.item.name
      this.newUrl = val.item.url
      this.editIndex = val.index
    }
  }
}
</script>

<style lang="scss">
.bookmark {
  max-width: 960px;
  margin: 0 auto;
}
</style>
