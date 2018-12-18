<template>
	<section class="top">
	<div>
		<div style="float: left;">
			<span style="color: #FFFFFF;padding-left: 10px;font-size: 20px;">杭州迅安经营管理系统</span>
		</div>
<div style="position: absolute;right: 20px;">
	<el-dropdown trigger="hover"  style="margin-right: 20px;"   @click="handleClick">
	<span class="el-dropdown-link">
		<el-badge :value="12" class="item">
	<i class="el-icon-bell" style="color: #FFFFFF;font-size: 20px;"></i>
	
	</el-badge>
	
	</span>
	<el-dropdown-menu slot="dropdown" class="topDropdown"   @command="handleClick">
		<div  style='height: 300px; auto;overflow-x:overlay;'>
			<el-dropdown-item class="clearfix" >
				<span  @click="handleClick">设备检修提醒：123456<el-badge class="mark" is-dot /></span>
			</el-dropdown-item>
			<el-dropdown-item class="clearfix"  @click="handleClick">
			<span  @click="handleClick">设备检修提醒：123456<el-badge class="mark" is-dot /></span>
			</el-dropdown-item>
			<el-dropdown-item class="clearfix"  @click="handleClick">
			<span  @click="handleClick">设备检修提醒：123456<el-badge class="mark" is-dot /></span>
			</el-dropdown-item>
			<el-dropdown-item class="clearfix"  @click="handleClick">
			<span  @click="handleClick">设备检修提醒：123456<el-badge class="mark" is-dot /></span>
			</el-dropdown-item>
			<el-dropdown-item class="clearfix"  @click="handleClick">
			<span  @click="handleClick">设备检修提醒：123456<el-badge class="mark" is-dot /></span>
			</el-dropdown-item>
			<el-dropdown-item class="clearfix"  @click="handleClick">
			<span  @click="handleClick">设备检修提醒：123456<el-badge class="mark" is-dot /></span>
			</el-dropdown-item>
			<el-dropdown-item class="clearfix"  @click="handleClick">
			<span  @click="handleClick">设备检修提醒：123456<el-badge class="mark" is-dot /></span>
			</el-dropdown-item>
		</div>
		<div style="text-align: center;"   @click="handleClick"><el-button type="text">查看全部</el-button></div>
	</el-dropdown-menu>
	</el-dropdown>
		<el-dropdown class="avatar-container" trigger="click" style="color: #FFFFFF;">
			<div class="avatar-wrapper">
				<span style="line-height: 50px;">设置<i class="el-icon-caret-bottom" /></span>
			</div>
			<el-dropdown-menu slot="dropdown" class="user-dropdown">
				<router-link class="inlineBlock" to="/">
					<el-dropdown-item>
						首页
					</el-dropdown-item>
				</router-link>
				<el-dropdown-item divided>
					<span style="display:block;" @click="logout">退出</span>
				</el-dropdown-item>
			</el-dropdown-menu>
		</el-dropdown>
		
			
		</div>
			
	</div>
	</section>
</template>

<script>
	import {
		mapGetters
	} from 'vuex'
	import Breadcrumb from '@/components/Breadcrumb'
	import Hamburger from '@/components/Hamburger'

	export default {
		components: {
			Breadcrumb,
			Hamburger
		},
		computed: {
			...mapGetters([
				'sidebar',
				'avatar'
			])
		},
		methods: {
			toggleSideBar() {
				this.$store.dispatch('ToggleSideBar')
			},
			logout() {
				this.$store.dispatch('LogOut').then(() => {
					location.reload() // 为了重新实例化vue-router对象 避免bug
				})
			},
			handleClick() {
				this.$router.push('/message/index');
      }
		}
	}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
	.top {
		position: fixed;
		
		top: 0;
		left: 0;
		width: 100%;
		height: $topNavHeight;
		line-height: $topNavHeight;
		border-radius: 0px !important;
		background: rgb(26, 119, 207);
		border-bottom: none;
		z-index: 1001;
	}
	
</style>
