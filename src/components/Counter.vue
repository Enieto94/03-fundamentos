<template>
  <h2>{{customTitle}}</h2>
  <p>{{counter}}= {{squareCounter}} <sup>2</sup></p>
  <!-- <p>{{counter}} <sup>2</sup> = {{getSquareValue()}}</p> -->

  <!-- <p>Has published books</p> -->
  <!-- <span>{{publishedBooksMessage}}</span> -->
  <div>
	  <button @click="increase">+1</button>
	  <button @click="decrease">-1</button>
  </div>


</template>

<script>
export default {
	// Tres tipos de props
	/*
		1. Prop: Number
		2. Arrays ['title'] <Component title="nombre" />
		3. props: {prop: type}
	*/
	props: {
		title: String,
		start: {
			type: Number,
			required: true,
			 default: 100,
			 validator(value){
				 return value >= 100

			 }
		}
	},
	data() {
		// return {author: {
		// 	name: 'John Doe',
		// 	books: [
		// 		'Vue 2 - Advanced Guide',
		// 		'Vue 3 - Advanced Guide',
		// 		'Vue 2 - Other Guide'
		// 	]
		// 	}
		return{

			counter: this.start
		}

	},
	methods: {
		getSquareValue() {
			return this.counter * this.counter
		},
		increase() {
			this.counter++
		},
		decrease(){
			this.counter--
		}
	},
	computed: {
		// publishedBooksMessage() {
		// 	return this.author.books.length > 0 ? 'Yes' : 'No'
		// }
		squareCounter() {
			console.log('computed squareCounter')
			return this.counter * this.counter
		},
		customTitle() {
			// return this.title ? this.title : 'counter'
			return this.title || 'Counter'
		}
	}
}
</script>

<style>
button{
	background-color: #64BB87;
	border-radius: 5px;
	border: 1px solid white;
	color: white;
	cursor: pointer;
	margin: 0 5px;
	padding: 5px 15px;
	transition: 0.3s ease-in;
}
button:hover{
	background-color: #5aa67b;
	transition: 0.3s ease-in-out;
}
</style>