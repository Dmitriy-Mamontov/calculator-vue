<template>
	<button 
	:class="{
		'number-button': look === 'number', 
		'action-button': look === 'operator'
	}"
	@click="$emit('click', value)"
	>
	{{ value }}
	</button>
	
</template>
<script>
export default {
	emits:['click'],
	props:{
		look:{
			type:String,
			default:'number'
		},

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

			.action-button{
				color: black;
				padding: 0;
				background: rgb(255, 190, 116);
				cursor:pointer;
				border-width: 1px;
			}
</style>