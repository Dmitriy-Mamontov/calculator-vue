<template>
<BaseButton @click="transferInput" :look="'operator'" @clickButtton="allClean" value="AC"/>
<BaseButton @click="transferInput" :look="'operator'" @clickButtton="squareRoot" value="√"/>
<BaseButton @click="transferInput" :look="'operator'" @clickButtton="calcPercent" value="%"/>
<BaseButton @click="transferInput" :look="'operator'" @clickButtton="addOperator" value="/"/>

<BaseButton @click="transferInput" @clickButtton="addNumber" value="7"/>
<BaseButton @click="transferInput" @clickButtton="addNumber" value="8"/>
<BaseButton @click="transferInput" @clickButtton="addNumber" value="9"/>
<BaseButton @click="transferInput" :look="'operator'" @clickButtton="addOperator" value="*"/>

<BaseButton @click="transferInput" @clickButtton="addNumber" value="4"/>
<BaseButton @click="transferInput" @clickButtton="addNumber" value="5"/>
<BaseButton @click="transferInput" @clickButton="addNumber" value="6"/>
<BaseButton @click="transferInput" :look="'operator'" @clickButton="addOperator" value="-"/>

<BaseButton @click="transferInput" @clickButtton="addNumber" value="1"/>
<BaseButton @click="transferInput" @clickButtton="addNumber" value="2"/>
<BaseButton @click="transferInput" @clickButtton="addNumber" value="3"/>
<BaseButton :look="'operator'" @click="transferInput" @clickButtton="addOperator" value="+"/>

<BaseButton @click="transferInput" @clickButtton="addNumber" value="0"/>
<BaseButton @click="transferInput" @clickButtton="addNumber" value="."/>
<BaseButton :look="'operator'" @click="transferInput" @clickButtton="deleteLastSymbol" value="del."/>
<BaseButton :look="'operator'" @click="transferInput" @clickButtton="showResult" value="="/>
</template>

<script> 
import BaseButton from './BaseButton.vue'

export default{
	name:'BaseButtons',
	emits:['transferInput'],
	components:{
		BaseButton,
	},
	data(){
		return{
			inputValue:'',
			value: '',
			shadowValue:'',
			memory:[],
			operators:['+','-', '*', '/'],
			numbers:['1','2','3','4','5','6','7','8','9','0','.']
		}
	},
	methods:{

		transferInput(){
			this.$emit('transferInput', this.inputValue)
		},

		addNumber(data){
			this.value += data
			this.shadowValue += data
			this.inputValue += Object.values(data)
		},

		allClean(){
			this.memory = []
			this.value = ''
			this.shadowValue = ''
			this.inputValue = ''
		},

		addOperator(data){
			if(this.shadowValue !== ''){
				this.memory.push(this.shadowValue)
			}
			this.value += data
				for(let i=0; i <= this.memory.length; i++){
					if(this.memory[i] === this.operators[0]){
						let res = Number(this.memory[i-1]) + Number(this.memory[i+1])
						this.shadowValue = res
						this.memory=[]
						this.memory.push(res)
					}else if(this.memory[i] === this.operators[1]){
						let res = Number(this.memory[i-1]) - Number(this.memory[i+1])
						this.shadowValue = res
						this.memory=[]
						this.memory.push(res)
					}else if(this.memory[i] === this.operators[2]){
						let res = this.memory[i-1] * this.memory[i+1]
						this.shadowValue = res
						this.memory=[]
						this.memory.push(res)
					}else if(this.memory[i] === this.operators[3]){
						let res = this.memory[i-1] / this.memory[i+1]
						this.shadowValue = res
						this.memory=[]
						this.memory.push(res)
					}
				}
			this.memory.push(data)
			this.shadowValue = ''
			this.inputValue += Object.values(data)
		},

		showResult(){
			this.memory.push(this.shadowValue)
			for(let i=0; i <= this.memory.length; i++){
				if(this.memory[i] === this.operators[0]){
					let res = Number(this.memory[i-1]) + Number(this.memory[i+1])
					this.value = res
					this.shadowValue = res
					this.memory=[]
					this.memory.push(res)
					this.inputValue = res
				}else if (this.memory[i] === this.operators[1]){
					let res = Number(this.memory[i-1]) - Number(this.memory[i+1])
					this.value = res
					this.shadowValue = res
					this.memory=[]
					this.memory.push(res)
					this.inputValue = res
				}else if (this.memory[i] === this.operators[2]){
					let res = this.memory[i-1] * this.memory[i+1]
					this.value = res
					this.shadowValue = res
					this.memory=[]
					this.memory.push(res)
					this.inputValue = res
				}else if (this.memory[i] === this.operators[3]){
					let res = this.memory[i-1] / this.memory[i+1]
					this.value = res
					this.shadowValue = res
					this.memory=[]
					this.memory.push(res)
					this.inputValue = res
				}
			}
		},

		squareRoot(){
			this.value = Math.sqrt(this.value);
			this.shadowValue = this.value;
			this.memory.push(this.shadowValue)
			this.inputValue = this.value
		},

		calcPercent(){
			this.shadowValue = this.memory[0] * this.shadowValue / 100
			this.memory.push(this.shadowValue)
			for(let i=0; i<=this.operators.length; i++){
				if(this.memory[i] === this.operators[0]){
					let res = Number(this.memory[i-1]) + Number(this.memory[i+1])
					this.value = res
					this.shadowValue = res
					this.memory=[]
					this.memory.push(res)
					this.inputValue = res
				}else if(this.memory[i] === this.operators[1]){
					let res = Number(this.memory[i-1]) - Number(this.memory[i+1])
					this.value = res
					this.shadowValue = res
					this.memory=[]
					this.memory.push(res)
					this.inputValue = res
				}else if(this.memory[i] === this.operators[2]){
					let res = Number(this.memory[i-1]) * Number(this.memory[i+1] / 100)
					this.value = res
					this.shadowValue = res
					this.memory=[]
					this.memory.push(res)
					this.inputValue = res
				}else if(this.memory[i] === this.operators[3]){
					let res = Number(this.memory[i-1]) / Number(this.memory[i+1] / 100)
					this.value = res
					this.shadowValue = res
					this.memory=[]
					this.memory.push(res)
					this.inputValue = res
				}
			}
		},

		deleteLastSymbol(){
			if(this.memory.length === 1){
				this.memory =[]
			}
			for(let i=0; i <= this.numbers.length; i++){
				if(this.value[this.value.length-1] === this.numbers[i]){
					this.value = this.value.slice(0,-1)
					this.shadowValue = this.shadowValue.slice(0,-1)
					this.inputValue = this.value
				}
			}
			for(let i=0; i <= this.operators.length; i++){
				if(this.memory[this.memory.length-1] === this.operators[i] && this.shadowValue === ''){
					this.memory.pop()
					this.value = this.value.slice(0,-1)
					this.inputValue = this.value
				}
			}
		}
	},
}
</script>