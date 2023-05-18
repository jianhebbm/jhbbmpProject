<script>
	if(window.innerWidth>750){
	    window.innerWidth=750;  
	}  
	export default {
		globalData:{
			// apihost:"https://api.jianhebbm.com",
			apihost:"http://localhost:54109",
			accountUserInfo:{},
		},
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	
</style>
