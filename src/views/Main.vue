<template>
  <el-container style="height: 100%">
    <el-aside width="200px"><Aside /></el-aside>
    <el-container>
      <el-header><Header /></el-header>
      <Tab />
      <el-main><router-view></router-view></el-main>
    </el-container>
  </el-container>
</template>

<script>
import Header from '../components/common/Header'
import Aside from '../components/common/Aside'
import Tab from '../components/common/Tab'

export default {
  name: 'Main',
  components: {
    Header,
    Aside,
    Tab
  }
}
</script>

<style lang="scss" scoped>
.el-header {
  background: #333;
}
</style>
