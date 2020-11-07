<template>
	<div id="app">
		<el-container>
			<el-header>
				<div id="logo">
					<img src="/static/timg.jpg">
				</div>
				<el-radio-group v-model="isCollapse" id="spread">
					<el-radio-button :label="false"><i class="el-icon-s-unfold"></i></el-radio-button>
					<el-radio-button :label="true"><i class="el-icon-s-fold"></i></el-radio-button>
				</el-radio-group>
			</el-header>
			<el-container>
				<el-aside width="250px">
					<el-menu default-active="2" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose" :collapse="false">
						<el-submenu index="1">
							<template slot="title">
								<i class="el-icon-location"></i>
								<span slot="title" class="test">娱乐资源</span>
							</template>
							<el-menu-item-group>
								<el-menu-item index="1-1"><span class="test1"> <i class="el-icon-camera"></i>在线视频</span></el-menu-item>
								<el-menu-item index="1-2"><span class="test1"> <i class="el-icon-video-camera"></i>电影下载</span></el-menu-item>
								<el-menu-item index="1-3"><span class="test1"> <i class="el-icon-upload"></i>视频下载</span></el-menu-item>
							</el-menu-item-group>
						</el-submenu>
						<el-submenu index="2">
							<template slot="title">
								<i class="el-icon-menu"></i>
								<span slot="title" class="test">学习资料</span>
							</template>
							<el-menu-item-group>
								<el-menu-item index="2-1"><span class="test1"><i class="el-icon-files"></i>技术社区</span></el-menu-item>
								<el-menu-item index="2-2"><span class="test1"><i class="el-icon-collection"></i>电子书</span></el-menu-item>
							</el-menu-item-group>
						</el-submenu>
						<el-submenu index="3">
							<template slot="title">
								<i class="el-icon-document"></i>
								<span slot="title" class="test">学术资源</span>
							</template>
							<el-menu-item-group>
								<el-menu-item index="3-1"><span class="test1"><i class="el-icon-crop"></i>写作工具</span></el-menu-item>
								<el-menu-item index="3-2"><span class="test1"><i class="el-icon-search"></i>论文搜索</span></el-menu-item>
								<el-menu-item index="3-3"><span class="test1"><i class="el-icon-monitor"></i>PPT工具</span></el-menu-item>
							</el-menu-item-group>
						</el-submenu>
						<el-submenu index="4">
							<template slot="title">
								<i class="el-icon-setting"></i>
								<span slot="title" class="test">实用软件</span>
							</template>
							<el-menu-item-group>
								<el-menu-item index="4-1"><span class="test1"><i class="el-icon-data-board"></i>电脑软件</span></el-menu-item>
								<el-menu-item index="4-2"><span class="test1"><i class="el-icon-mobile-phone"></i>手机软件</span></el-menu-item>
								<el-menu-item index="4-3"><span class="test1"><i class="el-icon-mobile"></i>科学上网</span></el-menu-item>
								<el-menu-item index="4-4"><span class="test1"><i class="el-icon-s-grid"></i>综合导航</span></el-menu-item>
								<el-menu-item index="4-5"><span class="test1"><i class="el-icon-s-data"></i>资源分享</span></el-menu-item>
							</el-menu-item-group>
						</el-submenu>
					</el-menu>
				</el-aside>
				<el-main>
					<el-form ref="numberValidateForm" :model="numberValidateForm" label-position="left" label-width="80px" style="margin: 20px;">
						<el-form-item label="志愿名称" size="small">
							<el-col :span="9">
								<el-input v-model="form.name"></el-input>
							</el-col>
						</el-form-item>
						<el-form-item label="志愿地点" size="small" style="margin-right: 1000px;">
							<el-select v-model="form.region" placeholder="请选择志愿区域">
								<el-option label="老年大学" value="old_University"></el-option>
								<el-option label="青山湖小学" value="qsh_school"></el-option>
								<el-option label="食堂" value="dinner_Hall"></el-option>
								<el-option label="操场" value="playground"></el-option>
								<el-option label="火车站" value="train_station"></el-option>
							</el-select>
						</el-form-item>
						<el-form-item label="志愿时间" size="small">
							<el-col :span="6">
								<el-date-picker type="date" placeholder="选择日期" v-model="form.date1" style="width: 100%;"></el-date-picker>
							</el-col>
							<el-col class="line" :span="2">--------</el-col>
							<el-col :span="6">
								<el-time-picker placeholder="选择时间" v-model="form.date2" style="width: 100%;"></el-time-picker>
							</el-col>
						</el-form-item>
						<el-form-item label="学号" prop="num" :rules="[
				        { required: true, message: '学号不能为空'},
				        { type: 'number', message: '学号必须为数字值'}
				      ]"
						 size="small">
							<el-col :span="9">
								<el-input type="age" v-model.number="numberValidateForm.number" autocomplete="off"></el-input>
							</el-col>
						</el-form-item>
						<el-form-item label="姓名" size="small" :rules="[
						        { required: true, message: '姓名不能为空'}]">
							<el-col :span="9">
								<el-input v-model="form.stu_name"></el-input>
							</el-col>
						</el-form-item>
						<el-form-item label="班级" size="small" :rules="[
						        { required: true, message: '班级不能为空'}]">
							<el-col :span="9">
								<el-input v-model="form.class_name"></el-input>
							</el-col>
						</el-form-item>

						<el-form-item label="年龄" prop="age" :rules="[
						        { required: true, message: '年龄不能为空'},
						        { type: 'number', message: '年龄必须为数字值'}
						      ]"
						 size="small">
							<el-col :span="9">
								<el-input type="age" v-model.number="numberValidateForm.age" autocomplete="off"></el-input>
							</el-col>
						</el-form-item>
						<el-form-item style="float: left;margin-left: 20px;">
							<el-button type="primary" @click="submitForm('numberValidateForm')" style="margin-right: 20px;">提交</el-button>
							<el-button @click="resetForm('numberValidateForm')" style="margin-left: 20px;">重置</el-button>
						</el-form-item>
					</el-form>
				</el-main>
			</el-container>
		</el-container>
	</div>
</template>
<style>
	html,
	body {
		height: 100%;
		width: 100%;
	}

	.el-header,
	.el-footer {
		height: 20%;
	}

	#logo {
		width: 250px;
		height: 200px;
		float: left;
	}

	#logo img {
		width: 200px;
		height: 80px;
		float: left;
		margin-bottom: 10px;
	}

	.test {
		margin-right: 40px;
		margin-bottom: 0px;

	}

	.test1 {
		margin-right: 10px;
		margin-top: 0px;
	}

	.el-menu-item-group {
		background-color: whitesmoke;
	}

	.active {
		display: none;
	}

	#spread {
		float: left;
		display: none;
	}


	.el-aside {
		background-color: whitesmoke;
		line-height: 100px;
		overflow-x: hidden;
		margin-top: 10px;
	}

	.el-main {
		background-color: #E9EEF3;
		color: #333;
		text-align: center;
		line-height: 160px;
		margin-top: 10px;
	}

	body>.el-container {
		margin-bottom: 40px;
	}

	.el-menu-vertical-demo:not(.el-menu--collapse) {
		width: 250px;
		min-height: 800px;
		background-color: whitesmoke;
		margin-top: 20px;
	}
	.el-menu--collapse {
		background-color: whitesmoke;
	}
</style>

<script>
	export default {
		data() {
			const item = {
				date: '',
				name: '',
				address: ''
			};
			return {
				sizeForm: {
					name: 'App',
					region: ''
				},
				numberValidateForm: {
					age: ''
				},
				tableData: Array(20).fill(item),
				isCollapse: true,
				isActive: true,
				form: {
					name: '',
					region: '',
					date1: '',
					date2: '',
					delivery: false,
					type: [],
					resource: '',
					desc: ''
				}
			};
		},
		methods: {
			onSubmit() {
				console.log('submit!');
			},
			submitForm(formName) {
				this.$refs[formName].validate((valid) => {
					if (valid) {
						alert('submit!');
					} else {
						console.log('error submit!!');
						return false;
					}
				});
			},
			resetForm(formName) {
				this.$refs[formName].resetFields();
			},
			goBack() {
				console.log('go back');
			},
			handleOpen(key, keyPath) {
				console.log(key, keyPath);
			},
			handleClose(key, keyPath) {
				console.log(key, keyPath);
			},
			checkitem(isActive) {
				this.isActive = !isActive;
			}
		}
	};
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		display: flex;
	}
</style>
