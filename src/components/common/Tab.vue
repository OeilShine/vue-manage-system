<template>
  <div class="tabs">
    <el-tag
      :key="tag.name"
      v-for="tag in tags"
      size="small"
      :closable="tag.name !== 'home'"
      :disable-transitions="false"
      @close="handleClose(tag)"
      @click="changeMenu(tag)"
    >
      {{ tag.label }}
    </el-tag>
  </div>
</template>

<script>
import { mapState, mapMutations } from 'vuex'
export default {
  name: 'Tab',
  data() {
    return {
      dynamicTags: ['标签一', '标签二', '标签三']
    }
  },
  computed: {
    ...mapState({
      tags: state => state.tab.tabsList
    })
  },
  methods: {
    ...mapMutations({
      close: 'closeTab'
    }),
    handleClose(tag) {
      this.close(tag)
    },
    changeMenu(item) {
      this.$router.push({ name: item.name })
      this.$store.commit('selectMenu', item)
    }
  }
}
</script>

<style lang="scss" scoped>
.el-tag + .el-tag {
  margin-left: 10px;
}
.button-new-tag {
  margin-left: 10px;
  height: 32px;
  line-height: 30px;
  padding-top: 0;
  padding-bottom: 0;
}
.tabs {
  padding: 20px;
  .el-tag {
    margin-right: 15px;
  }
}
</style>
