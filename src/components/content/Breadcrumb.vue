<template>
  <div>
    <el-breadcrumb separator-class="el-icon-arrow-right">
      <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
      <el-breadcrumb-item :to="current.path" v-if="current">{{ current.label }}</el-breadcrumb-item>
    </el-breadcrumb>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  name: 'Breadcrumb',
  computed: {
    ...mapState({
      current: state => state.tab.currentMenu
    })
  }
}
</script>

<style lang="scss" scoped></style>

<style lang="scss">
.el-breadcrumb {
  width: 100%;
  height: 26px;
  line-height: 26px;
  margin-bottom: 20px;
  padding-left: 12px;
  // background: #e8e8e8;
  border-bottom: 1px #e0e0e0 solid;
}
.el-breadcrumb__inner a,
.el-breadcrumb__inner.is-link,
.el-breadcrumb__item:last-child .el-breadcrumb__inner,
.el-breadcrumb__item:last-child .el-breadcrumb__inner a {
  font-weight: 700;
  color: rgb(117, 111, 111);
}
.el-breadcrumb__item:last-child .el-breadcrumb__inner a:hover,
.el-breadcrumb__item:last-child .el-breadcrumb__inner:hover {
  font-weight: 700;
  color: #409eff;
}
</style>
