<template>
  <header>
    <div class="l-content">
      <el-button type="primary" icon="el-icon-menu" size="mini"></el-button
      ><el-breadcrumb separator-class="el-icon-arrow-right">
        <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
        <el-breadcrumb-item :to="current.path" v-if="current">{{ current.label }}</el-breadcrumb-item>
      </el-breadcrumb>
    </div>
    <div class="r-content">
      <el-dropdown trigger="click">
        <span class="el-dropdown-link"><img :src="userImg" class="userImg" alt=""/></span>
        <el-dropdown-menu slot="dropdown">
          <el-dropdown-item icon="el-icon-orange">个人中心</el-dropdown-item>
          <el-dropdown-item icon="el-icon-s-promotion">退出</el-dropdown-item>
        </el-dropdown-menu>
      </el-dropdown>
    </div>
  </header>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'Header',
  data() {
    return {
      userImg: require('@/assets/images/userMan.jpg')
    }
  },
  computed: {
    ...mapState({
      current: state => state.tab.currentMenu
    })
  }
}
</script>

<style lang="scss" scoped>
header {
  display: flex;
  height: 100%;
  align-items: center;
  justify-content: space-between;
}
.l-content {
  display: flex;
  align-items: center;
  .el-button {
    margin-right: 20px;
  }
}
.r-content {
  .userImg {
    width: 48px;
    height: 48px;
    border-radius: 50%;
  }
}
</style>

<style lang="scss">
.el-breadcrumb__inner a,
.el-breadcrumb__inner.is-link,
.el-breadcrumb__item:last-child .el-breadcrumb__inner,
.el-breadcrumb__item:last-child .el-breadcrumb__inner a {
  font-weight: 700;
  color: #fff;
}
.el-breadcrumb__item:last-child .el-breadcrumb__inner a:hover,
.el-breadcrumb__item:last-child .el-breadcrumb__inner:hover {
  font-weight: 700;
  color: #409eff;
}
</style>
