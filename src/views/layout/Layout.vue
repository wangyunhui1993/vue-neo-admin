<template>
	<section class="layout">
	<Top/>
	<div  class="app-wrapper">
		<div :class="classObj" style="position: relative;">
			<div v-if="device==='mobile'&&sidebar.opened" class="drawer-bg" @click="handleClickOutside"/>
			<sidebar class="sidebar-container"/>
			<div class="main-container">
				<navbar/>
        <tags-view/>
				<app-main/>
			</div>
		</div>
	</div>
  
	</section>
</template>

<script>
import { Navbar, Sidebar, AppMain ,Top ,TagsView} from './components'
import ResizeMixin from './mixin/ResizeHandler'

export default {
  name: 'Layout',
  components: {
    Navbar,
    Sidebar,
    AppMain,
    Top,
    TagsView
  },
  mixins: [ResizeMixin],
  computed: {
    sidebar() {
      return this.$store.state.app.sidebar
    },
    device() {
      return this.$store.state.app.device
    },
    classObj() {
      return {
        hideSidebar: !this.sidebar.opened,
        openSidebar: this.sidebar.opened,
        withoutAnimation: this.sidebar.withoutAnimation,
        mobile: this.device === 'mobile'
      }
    }
  },
  methods: {
    handleClickOutside() {
      this.$store.dispatch('CloseSideBar', { withoutAnimation: false })
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
  @import "src/styles/mixin.scss";
  .app-wrapper {
    @include clearfix;
    position: absolute;
		top:$topNavHeight;
		bottom:0;
    width: 100%;
		overflow-y: auto;
		
    &.mobile.openSidebar{
      position: fixed;
      top: 0;
    }
  }
  .drawer-bg {
    background: #000;
    opacity: 0.3;
    width: 100%;
    top: 0;
    height: 100%;
    position: fixed;
    z-index: 999;
  }
	.layout-main{
		padding: 0;
	}
	.layout-header{
		padding: 0;
	}
</style>
