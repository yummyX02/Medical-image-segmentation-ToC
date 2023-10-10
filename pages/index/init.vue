<template>
</template>

<script>
	export default {
		data() {
			return {
				token:'',
				value:'',
			}
		},
		

		onLoad() {
			uni.getStorage({
				key:"launchFlag",
				success: function (res) {
				        value = res.data;
				        resolve();
				      },
				      fail: function (err) {
				        value = err.data;
				        resolve(); // 不管失败与否，都继续执行
				      }
			})
		
		  使用Promise.all等待所有异步操作完成
		  Promise.all([
		    new Promise((resolve, reject) => {
		      uni.getStorage({
		        key: 'launchFlag',
		        success: function (res) {
		          value = res.data;
		          resolve();
		        },
		        fail: function (err) {
		          value = err.data;
		          resolve(); // 不管失败与否，都继续执行
		        }
		      });
		    }),
		    new Promise((resolve, reject) => {
		      uni.getStorage({
		        key: 'access_token',
		        success: function (res) {
		          token = res.data;
		          resolve();
		        },
		        fail: function (err) {
		          resolve(); // 不管失败与否，都继续执行
		        }
		      });
		    })
		  ]).then(() => {
		    // 所有异步操作完成后执行此处代码
		    checkValueAndToken();
		  });
		  
		  function checkValueAndToken() {
		    // 剩下的逻辑和之前一样
		    if (value !== '' && token !== '') {
		      console.log("不是第一次进入app");
		      if (token) {
		        console.log("有token");
		        setTimeout(function () {
		          uni.switchTab({
		            url: '/pages/index/home',
		          });
		        }, 100);
		      } else {
		        console.log("没有token，即将跳转登录页");
		        setTimeout(function () {
		          console.log("diaoyong")
		          uni.reLaunch({
		            url: '/pages/login/login',
		          });
		        }, 100);
		      }
		    } else if (value === '') {
		      // 没有值，跳到引导页，并存储，下次打开就不会进去引导页
		      uni.setStorage({
		        key: 'launchFlag',
		        data: true
		      });
		      uni.redirectTo({
		        url: '/pages/index/guide'
		      });
		    }
		  }
		}

	}
</script>

<style>
</style>