<template>
		<main>
			<div class="wrapper">
				<input class="word" v-model="inputValue" placeholder="0" />
			</div>
			<div class="keyboard">
				<operators-button @click="allClean" value="AC"></operators-button>
				<operators-button @click="squareRoot" value="√"></operators-button>
				<operators-button @click="calcPercent" value="%"></operators-button>
				<operators-button @click="addOperator" value="/"></operators-button>

				<numbers-button @click="addNumber" value="7"></numbers-button>
				<numbers-button @click="addNumber" value="8"></numbers-button>
				<numbers-button @click="addNumber" value="9"></numbers-button>
				<operators-button @click="addOperator" value="*"></operators-button>

				<numbers-button @click="addNumber" value="4"></numbers-button>
				<numbers-button @click="addNumber" value="5"></numbers-button>
				<numbers-button @click="addNumber" value="6"></numbers-button>
				<operators-button @click="addOperator" value="-"></operators-button>

				<numbers-button @click="addNumber" value="1"></numbers-button>
				<numbers-button @click="addNumber" value="2"></numbers-button>
				<numbers-button @click="addNumber" value="3"></numbers-button>
				<operators-button @click="addOperator" value="+"></operators-button>

				<numbers-button @click="addNumber" value="0"></numbers-button>
				<numbers-button @click="addNumber" value="."></numbers-button>
				<operators-button @click="deleteLastSymbol" value="del."></operators-button>
				<operators-button @click="showResult" value="="></operators-button>
			</div>
		</main>
</template>
<!--          TODO: Сделай переиспользуемый компонент кнопки, компоненты хранятся в папке components #--> 


<script>
import NumbersButton from './components/NumbersButton.vue'
import OperatorsButton from './components/OperatorsButton.vue'
export default{
  // TODO: Убери неиспользуемый код (комментарии)#
	components:{
		NumbersButton,
		OperatorsButton
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
		// TODO: Пробелы не нужны после объявления методов (+ if else конструкции (else пишется на той же строке, где заканчивается if)#)
    // TODO: Между методами 1 вместо 2
	},

// TODO: Убери ненужные пробелы#
}
</script>
<!--TODO: Стили пишутся везде с атрибутом scoped #-->
<!-- /* TODO: Сделай для одной страницы названия классов в стиле БЭМ +
добавь в тег style атрибут lang="scss", используя препроцессор, перепиши стили для калька
*/ -->
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