<template>
	<BaseWrapper>
			<template #input >
				<BaseInput v-model="input"/>
			</template>
			<template #keyboard>
				<BaseButtons @transferInput="changeInput"/> 
			</template>
	</BaseWrapper>
</template>

<script>

import BaseWrapper from './components/BaseWrapper.vue'
import BaseButtons from './components/BaseButtons.vue'
import BaseInput from './components/BaseInput.vue'

export default{
	components:{
		BaseWrapper,
		BaseButtons,
		BaseInput,
	},

	data(){
		return{
			input:'',
		}
	},
	methods:{
		changeInput(data){
			this.input = data
		},
	},
}
</script>

<style lang="scss" scoped>
	@mixin wh ($w, $h){
		width:$w;
		height:$h;
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
</style>