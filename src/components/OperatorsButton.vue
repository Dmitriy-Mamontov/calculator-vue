<template>

	<button class="action-button" @click = "$emit('click', value)">{{ value }}</button>

</template>

<script>
export default {
	emits:['click'],

	props:{
		value:{
			type:[Number, String],
			required: true,
		}
	}
}

</script>

<style lang="scss" scoped>
	.action-button{
		color: black;
		padding: 0;
		background: rgb(255, 190, 116);
		cursor:pointer;
		border-width: 1px;
	}
</style>