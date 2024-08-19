	<template>
		<main>
			<div class="wrapper">
				<slot name="input"></slot>
			</div>
			<div class="keyboard">
				<slot name="keyboard"></slot>
			</div>
		</main>
</template>

<script>
export default {
name:'BaseWrapper'
}
</script>

<style lang="scss" scoped>

	@mixin wh ($w, $h){
		width:$w;
		height:$h;
	}
	html{
	@include wh(100%, 100%)
	}
	body{
		@include wh(100%, 100%);
		box-sizing: content-box
	}
	#app{
		@include wh(100%, 100%)
	}
	main{
		max-width:25%;
		min-width: 120px;
		margin: 150px auto;
		.wrapper{
			@include wh(100%, 50px);
			padding: 0;
		}
		.word{
			@include wh(100%, 100%);
			margin: 0;
			box-sizing: border-box;
			padding: 2px;
			border: 1px solid black;
			background-color: black;
			color:white;
			font-size: large;
		}
		.keyboard{
			width: 100%;
			height:auto;
			margin-top: 1px;
			display: grid;
			grid-template-columns: repeat(4, 1fr);
			grid-gap: 1px;
			grid-template-rows:repeat(5, 30px);
		}
	}
	@media (max-width:700px){
			main{
				max-width: 120px;
			}
		}


</style>