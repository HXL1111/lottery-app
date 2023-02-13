<template>
	<view class="content">
		<view class="number">{{number}}</view>
		<button v-show="isOver" @click="start">开始抽奖</button>
		<button v-show="!isOver" @click="stop">结束抽奖</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				number: 0,
				max: 100,
				min: 0,
				interval: 100,
				isOver: true,
				clock: null
			}
		},
		onLoad() {

		},
		methods: {
			start() {
				this.isOver = false
				this.clock = setInterval(() => {
					this.number = this.getRenderNumber()
				}, this.interval)
			},
			getRenderNumber() {
				return this.min + parseInt(Math.random() * (this.max - this.min))
			},
			stop() {
				this.isOver = true
				clearInterval(this.clock)
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
