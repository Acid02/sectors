<script>
	export default {
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
	/* #ifdef H5 */
	body{
		margin: 0;
		max-width: 750px;
		margin: 0 auto;
	}
	/* #endif */
</style>
