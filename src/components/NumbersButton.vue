<template>
	<button class="number-button" @click="$emit('click', value)"> {{ value }}</button>
</template>
<script>
export default {
	emits:['click'],
	props:{
		value:{
			type:[String, Number],
			required: true,
		}
	}
}
</script>

<style lang="scss" scoped>
	.number-button{
		color: black;
		padding: 0;
		background: rgb(172, 172, 172);
		cursor:pointer;
		border-width: 1px;
	}
</style>