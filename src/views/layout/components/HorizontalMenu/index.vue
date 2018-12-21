<template>
    <el-scrollbar wrap-class="scrollbar-wrapper">
      <!-- <el-menu
        :show-timeout="200"
        :default-active="$route.path"
        :collapse="isCollapse"
        mode="vertical"
        background-color="#304156"
        text-color="#bfcbd9"
        active-text-color="#409EFF"
      >
        <sidebar-item v-for="route in routes" :key="route.path" :item="route" :base-path="route.path"/>
      </el-menu> -->
      <el-menu
      :default-active="activeIndex2"
      class="el-menu-demo"
      mode="horizontal"
      @select="handleSelect"
      background-color="#304156"
      text-color="#f4f4f5"
      active-text-color="#409eff">
      <el-menu-item   v-for="route in routes" v-if="!route.hidden" :index="route.path"  :key="route.path">{{route.name}}</el-menu-item>
    </el-menu>



    </el-scrollbar>
  </template>
  
  <script>
  import { mapGetters } from 'vuex'
  
  export default {
    data() {
      return {
        activeIndex2: '1'
      };
    },
    methods: {
      handleSelect(key, keyPath) {
        this.$router.push(key);
      },

    },
    computed: {
      ...mapGetters([
        'sidebar'
      ]),
      routes() {
          console.log(this.$router.options.routes);
        return this.$router.options.routes
      },
      isCollapse() {
        return !this.sidebar.opened
      }
    }
  }
  </script>
  