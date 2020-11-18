<template>
	<div id="app">
		<div class="box">
			<ul v-for="(item,index) in orients" :key="index" :class="item">
				<li v-for="item in list" :key="item.index">{{item}}</li>
			</ul>
		</div>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				list: [1,2,3,4,5,6,7,8,9],
				orients: ["top","bottom","left","right","back","front"]
			}
		}
	}
</script>

<style lang="scss">
	* {
		margin: 0;
		padding: 0;
	}
	ul {
		list-style: none;
	}
	li {
		width: 60px;
		height: 60px;
		margin: 5px;
		line-height: 60px;
		text-align: center;
		float: left;
		font-size: 28px;
		font-weight: 700;
		border-radius: 10px;
		color: white;
	}
	#app {
		height: 100vh;
		display: flex;
		justify-content: center;
		align-items: center;
		.box {
			position: relative;
			perspective: 10000px;
			transform-style: preserve-3d;
			animation: rotate 10s linear infinite alternate;
			ul {
				width: 210px;
				margin: 10px;
				float: left;
				padding: 5px;
				position: absolute;
			}
			.top {
				transform: rotateX(90deg) translateZ(120px); 
				li {background: #D00000;}
			}
			.bottom {
				transform: rotateX(-90deg) translateZ(120px);
				li {background: #FAA307;}
			}
			.left {
				transform: rotateY(-90deg) translateZ(120px);
				li {background: #03045E;}
			}
			.right {
				transform: rotateY(90deg) translateZ(120px);
				li {background: #2B9348;}
			}
			.back {
				transform: translateZ(-120px);
				li {background: #5BC0BE;}
			}
			.front {
				transform: translateZ(120px);
				li {background: #0EAD69;}
			}
		}
	}
	@keyframes rotate {
		0% {transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);}
		20% {transform: rotateX(70deg) rotateY(70deg) rotate(70deg);}
		40% {transform: rotateX(140deg) rotateY(140deg) rotate(140deg);}
		60% {transform: rotateX(210deg) rotateY(210deg) rotate(210deg);}
		80% {transform: rotateX(280deg) rotateY(280deg) rotate(280deg);}
		100% {transform: rotateX(360deg) rotateY(360deg) rotate(360deg);}
	}
	
</style>
