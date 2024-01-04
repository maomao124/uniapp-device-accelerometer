<template>
	<view>
		<h2>x:{{x}}</h2>
		<h2>y:{{y}}</h2>
		<h2>z:{{z}}</h2>
		<button type="primary" @click="button1">监听加速度</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				x:0,
				y:0,
				z:0,
			}
		},
		methods: {
			button1()
			{
				uni.onAccelerometerChange(function(res)
				{
					this.x=res.x;
					this.y=res.y;
					this.z=res.z;
					console.log(this.x,this.y,this.z);
				})
			}
		}
	}
</script>

<style>

</style>
