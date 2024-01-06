<template>
	<view>
		<h2>x:{{x}}</h2>
		<h2>y:{{y}}</h2>
		<h2>z:{{z}}</h2>
		<button type="primary" @click="button1">注册监听加速度回调</button>
		<button type="primary" @click="button2">取消注册监听加速度回调</button>
		<button type="primary" @click="button3">开始监听加速度</button>
		<button type="primary" @click="button4">停止监听加速度</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				x:0.0,
				y:0.0,
				z:0.0,
				f:undefined,
			}
		},
		methods: {
			button1()
			{
				if(!this.f)
				{
					const that = this;
					this.f = function(res)
					{
						console.log(res);
						console.log(res.x,res.y,res.z);
						that.x=res.x;
						that.y=res.y;
						that.z=res.z;
					}
					uni.onAccelerometerChange(this.f)
				}
			},
			button2()
			{
				if(this.f)
				{
					uni.offAccelerometerChange(this.f);
					this.f=undefined;
				}
			},
			button3()
			{
				uni.startAccelerometer({
					interval:'normal',
					success: () => {
						uni.showToast({
							icon:'success',
							title:'成功'
						})
					},
					fail: () => {
						uni.showToast({
							title:'失败',
							icon:'fail',
						})
					}
				})
			},
			button4()
			{
				uni.stopAccelerometer({
					interval:'normal',
					success: () => {
						uni.showToast({
							icon:'success',
							title:'成功'
						})
					},
					fail: () => {
						uni.showToast({
							title:'失败',
							icon:'fail',
						})
					}
				})
			}
		}
	}
</script>

<style>
button{
	margin: 5px;
}
</style>
