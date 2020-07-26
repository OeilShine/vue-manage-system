<template>
  <el-menu
    default-active="2"
    class="el-menu-vertical-demo"
    @open="handleOpen"
    @close="handleClose"
    background-color="#2E2657"
    text-color="#fff"
    active-text-color="#ffd04b"
    :collapse="isCollage"
  >
    <el-menu-item :index="item.path" v-for="item in noChildren" :key="item.path" @click="clickMenu(item)">
      <i :class="'el-icon-' + item.icon"></i>
      <span slot="title">{{ item.label }}</span>
    </el-menu-item>
    <el-submenu :index="item.label" v-for="(item, index) in hasChildren" :key="index">
      <template slot="title">
        <i class="el-icon-s-help"></i>
        <span>{{ item.label }}</span>
      </template>
      <el-menu-item-group>
        <el-menu-item :index="subItem.path" v-for="(subItem, subIndex) in item.children" :key="subIndex" @click="clickMenu(subItem)"
          ><i :class="'el-icon-' + subItem.icon"></i><span>{{ subItem.label }}</span></el-menu-item
        >
      </el-menu-item-group>
    </el-submenu>
  </el-menu>

  <!-- <el-submenu :index="subItem.path" v-for="subItem in asideMenu" :key="subItem.id" @click="clickMenu(subItem)">
      <template slot="title">
        <i :class="'el-icon-' + subItem.icon"></i>
        <span>{{ subItem.label }}</span>
      </template>
      <el-menu-item :index="item.id" v-for="(item, index) in subItem.children" :key="index" @click="clickMenu(item)">
        <i :class="'el-icon-' + item.icon"></i>
        <span>{{ item.label }}</span>
      </el-menu-item>
    </el-submenu>
  </el-menu> -->
</template>

<script>
export default {
  name: 'Aside',
  data() {
    return {
      asideMenu: [
        {
          id: 1,
          name: 'home',
          path: '/',
          label: '首页',
          icon: 's-home'
        },
        {
          id: 2,
          name: 'video',
          path: '/video',
          label: '视频管理',
          icon: 'video-play'
        },
        {
          id: 3,
          name: 'user',
          path: '/user',
          label: '用户管理',
          icon: 'user'
        },
        {
          id: 4,
          name: 'other',
          label: '其他',
          path: '/other',
          icon: 'user',
          children: [
            {
              path: '/page1',
              name: 'page1',
              label: '演示页面1',
              icon: 'star-on'
            },
            {
              path: '/page2',
              name: 'page2',
              label: '演示页面2',
              icon: 'star-on'
            }
          ]
        }
      ]
    }
  },
  computed: {
    noChildren() {
      return this.asideMenu.filter(item => !item.children)
    },
    hasChildren() {
      return this.asideMenu.filter(item => item.children)
    },
    isCollage() {
      return this.$store.state.tab.isCollapse
    }
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath)
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath)
    },
    clickMenu(item) {
      this.$router.push({ name: item.name })
      this.$store.commit('selectMenu', item)
    }
  }
}
</script>

<style lang="scss" scoped>
.el-menu {
  height: 100%;
  border: none;
}
</style>
