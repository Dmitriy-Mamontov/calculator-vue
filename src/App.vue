<template>
		<main>
			<div class="wrapper">
				<input class="word" v-model="inputValue" placeholder="0" />
			</div>
			<the-button 
			@addNumber="addNumber"
			@allClean="allClean"
			@addOperator="addOperator"
			@showResult="showResult"
			@squareRoot="squareRoot"
			@calcPercent="calcPercent"
			@deleteLastSymbol="deleteLastSymbol"
			></the-button>
		</main>
</template>
<!--          TODO: Сделай переиспользуемый компонент кнопки, компоненты хранятся в папке components #--> 


<script>
import TheButton from '../Components/TheButton.vue'
export default{
  // TODO: Убери неиспользуемый код (комментарии)#
	components:{
		TheButton,
	},
	data(){
		return{
			inputValue:'',
		}
	},
	methods:{
		addNumber(data){
			this.inputValue = Object.values(data)
		},

		allClean(){
			this.inputValue = ''
		},

		addOperator(data){
			this.inputValue = Object.values(data)
		},

		showResult(data){
			this.inputValue = Object.values(data)
		},

		squareRoot(data){
			this.inputValue = Object.values(data)
		},

		calcPercent(data){
			this.inputValue = Object.values(data)
		},

		deleteLastSymbol(data){
			this.inputValue = Object.values(data)
		}
		// TODO: Пробелы не нужны после объявления методов (+ if else конструкции (else пишется на той же строке, где заканчивается if)#)
    // TODO: Между методами 1 вместо 2
	},

// TODO: Убери ненужные пробелы#
}
</script>
<!--TODO: Стили пишутся везде с атрибутом scoped #-->
/* TODO: Сделай для одной страницы названия классов в стиле БЭМ +
добавь в тег style атрибут lang="scss", используя препроцессор, перепиши стили для калька
*/
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
}
@media (max-width:700px){
		main{
			max-width: 120px;
		}
	}
/*TODO: стили прописываются по иерархии от большего к меньшему, html, body, #app, main, .classes, etc*/
				<input class="word" v-model="value" placeholder="0" />
			</div>
				<div class="keyboard">
<!--          TODO: Сделай переиспользуемый компонент кнопки, компоненты хранятся в папке components-->
					<button class="action-button" @click="allClean">AC</button>
					<button class="action-button" @click="squareRoot('√')">√</button>
					<button class="action-button" @click="calcPercent">%</button>
					<button class="action-button" @click="addOperator('/')">÷</button>

					<button class="number-button" @click="addNumber">7</button>
					<button class="number-button" @click="addNumber">8</button>
					<button class="number-button" @click="addNumber">9</button>
					<button class="action-button" @click="addOperator('*')">×</button>

					<button class="number-button" @click="addNumber">4</button>
					<button class="number-button" @click="addNumber">5</button>
					<button class="number-button" @click="addNumber">6</button>
					<button class="action-button" @click="addOperator('-')">-</button>

					<button class="number-button" @click="addNumber">1</button>
					<button class="number-button" @click="addNumber">2</button>
					<button class="number-button" @click="addNumber">3</button>
					<button class="action-button" @click="addOperator('+')">+</button>

					<button class="number-button" @click="addNumber">0</button>
					<button class="number-button" @click="addNumber">.</button>
					<button class="action-button-equal" @click="showResult">=</button>
				</div>
		</main>
</template>

<script>

export default{
  // TODO: Убери неиспользуемый код (комментарии)

	data(){
		return{
			value:'',
		// 	numbers:['1','2','3','4','5','6','7','8','9','0','.',],
		// 	actions:[ '+', '-', '*', '/' ],
		// 	a: '',
		// 	b: '',
		// 	c: '',
		}
	},


	methods:{
		// TODO: Пробелы не нужны после объявления методов (+ if else конструкции (else пишется на той же строке, где заканчивается if))
		addNumber(event){
			if(typeof(this.value) === 'number' ) {
				this.value = '' + event.target.textContent.toString()
			} else{
				this.value += event.target.textContent
			}
		},

		// addNumber(event){

			// if(this.b === '' && this.c === ''){
			// 	this.a += event.target.textContent
			// 	this.value = this.a
			// }

			// if(this.actions.includes(event.target.textContent.toString())){
			// 	this.c = event.target.textContent
			// 	this.value += this.c
			// }
			
			// else if(this.a !== '' && this.c !== ''){
			// 	this.b += event.target.textContent
			// 	this.value += this.b
			// }
    // TODO: Между методами 1 вместо 2
		

		allClean(){
			this.value = ''
		},

		addOperator(oper){
			this.value += oper
		},

    // TODO: функция eval не должна использоваться в коде
		showResult(){
			this.value = eval(this.value)
		},

		squareRoot(){
			this.value = Math.sqrt(this.value);
		},

		calcPercent(){
			this.value = this.value / 100;
			// const a = []
			// const b = []
			// const c = ''

		},
	
	},

// TODO: Убери ненужные пробелы

}
</script>

<!--TODO: Стили пишутся везде с атрибутом scoped-->
/* TODO: Сделай для одной страницы названия классов в стиле БЭМ +
добавь в тег style атрибут lang="scss", используя препроцессор, перепиши стили для калька
*/
<style lang="scss" scoped>
.action-button-equal{
  /* TODO: Пробел не нужен */
	grid-column-start: 3;
	grid-column-end: 5;
	color: black;
	padding: 0;
	background: rgb(255, 190, 116);
	cursor:pointer;
	border-width: 1px;

}

.wrapper{
	width: 100%;
	height:20%;
	padding: 0;
}

.word{
	height: 100%;
	width: 100% ;
	margin: 0;
	box-sizing: border-box;
	padding: 2px;
	border: 1px solid black;
	background-color: black;
	color:white;
	font-size: large;
}


.keyboard{
	height: 80%;
	width: 100% ;
	margin-top: 1px;
	display: grid;
	grid-template-columns: repeat(4, 1fr);
	grid-gap: 1px;
}

/*TODO: стили прописываются по иерархии от большего к меньшему, html, body, #app, main, .classes, etc*/
html{
	width: 100%;
	height: 100%;
}
body{
	width: 100%;
	height: 100%;
	margin:0;
}

#app{
	width: 100%;
	height: 100%;
}

main{
	width:30%;
	height: 50%;
	margin: 150px auto;
}

.action-button{
	color: black;
	padding: 0;
	background: rgb(255, 190, 116);
	cursor:pointer;
	border-width: 1px;
}

.number-button{
	color: black;
	padding: 0;
	background: rgb(172, 172, 172);
	cursor:pointer;
	border-width: 1px;

}
</style>