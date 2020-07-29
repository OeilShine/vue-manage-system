<template>
  <header>
    <div class="l-content">
      <el-button type="primary" icon="el-icon-menu" size="mini" @click="collapseMenu"></el-button>
      <div class="startshine-title">星辉后台管理系统</div>
    </div>
    <Tab />
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
import Tab from '../common/Tab'
export default {
  name: 'Header',
  data() {
    return {
      userImg: require('@/assets/images/userMan.jpg')
    }
  },
  components: {
    Tab
  },
  methods: {
    collapseMenu() {
      this.$store.commit('collapseMenu')
    }
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
.startshine-title {
  width: 230px;
  height: 30px;
  color: #ccc;
  font-weight: 700;
  font-size: 28px;
  font-family: '华文行楷';
}
.l-content {
  display: flex;
  align-items: center;
  .el-button {
    margin-right: 20px;
  }
}
.m-content {
  width: 50%;
}
.r-content {
  .userImg {
    width: 48px;
    height: 48px;
    border-radius: 50%;
  }
}
</style>
