<template>
  <el-container>
    <el-header><Header /></el-header>
    <el-container>
      <el-aside width="auto"><Aside /></el-aside>
      <el-main>
        <Breadcrumb />
        <router-view></router-view
      ></el-main>
    </el-container>
  </el-container>
</template>

<script>
import Header from '../components/common/Header'
import Aside from '../components/common/Aside'
import Breadcrumb from '../components/content/Breadcrumb'

export default {
  name: 'Main',
  components: {
    Header,
    Aside,
    Breadcrumb
  }
}
</script>

<style lang="scss" scoped>
.el-container {
  height: 100%;
}
.el-header {
  background: #170e45;
  padding-left: 10px;
}
.el-aside {
  height: 100%;
}
.el-menu-vertical-demo:not(.el-menu--collapse) {
  width: 200px;
  min-height: 400px;
}
.el-main {
  padding: 0;
}
</style>
