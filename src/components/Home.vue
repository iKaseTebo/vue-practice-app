<template>
	<div class="test">
		<input type="text" v-model="title">
		<h1>{{title}}</h1>
		<p v-if="showName">{{user.firstName}}</p>
		<p v-else v-text="user.lastName"></p>
	
		<button v-on:click="greet(title)">Greetings</button>
		<input type="text" v-on:keyup.enter="enterHit" v-on:keyup="pressKey"/>
		<ul>
			<li v-for="item in items">{{ item.title }}</li>
		</ul>

		<h3>{{fullName}}</h3>
		<label for="">First Name: </label>
		<input type="text" v-model="user.firstName"> <br />
		<label for="">Last Name: </label>
		<input type="text" v-model="user.lastName">
		<h2>{{msg}}</h2>
	</div>
</template>

<script>
	export default {
		name: 'Home',
		props: {
			msg: {
				type: String,
				default: 'Foobar'
			}
		},
		data() {
			return {
				title: 'Hello World',
				user: {
					firstName: 'John',
					lastName: 'Doe'
				},
				showName: true,
				items: [
					{ title:'Item One' },
					{ title:'Item Two' },
					{ title:'Item Three' },
					{ title:'Item Four' }
				]
			}
		},
		methods: {
			greet: function(greetings){
				alert(greetings);
			},
			pressKey: function(e){
				console.log(e.target.value);
			},
			enterHit: function(){
				console.log('You hit Enter');
			}

		},
		computed: {
			fullName: function(){
				return this.user.firstName+' '+this.user.lastName;
			}
		}
	}
</script>