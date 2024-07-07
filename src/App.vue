<template>
		<main>
			<div class="wrapper">
				<input class="word" v-model="value" placeholder="0" />
			</div>
				<div class="keyboard">
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
		
		addNumber(event){
			if(typeof(this.value) === 'number' ) {
				this.value = '' + event.target.textContent.toString()
			}

			else{
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

		

		allClean(){
			this.value = ''
		},

		addOperator(oper){
			this.value += oper
		},

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



}
</script>

<style>


.action-button-equal{

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