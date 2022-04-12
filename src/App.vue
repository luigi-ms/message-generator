<template>
	<div id="talkField">
		<header>
			<i class="fa-regular fa-circle-left fa-xl"></i>
			<h2>{{ title }}</h2>
			<i class="fa-solid fa-ellipsis-vertical fa-xl"></i>
		</header>
  
		<ul>
			<MessageComponent v-for="message in messages" v-bind:key="message.msg" :msg="message" />
		</ul>
	</div>
	
	<form>
		<label for="username">Nome do autor da mensagem</label>
		<input id="username" v-model="user" placeholder="Nome" />

		<label for="message">Corpo da mensagem</label>
		<input id="message" v-model="msg" placeholder="Mensagem"/>

		<label for="groupTitle">Nome do grupo</label>
		<input id="groupTitle" v-model="title" placeholder="Nome do grupo" />

		<button v-on:click.prevent="add">
			Adicionar
			<i class="fa-solid fa-paper-plane"></i>
		</button>
	</form>
</template>

<script>
import MessageComponent from './components/Message.vue';

export default {
  name: 'App',
	components: { MessageComponent },
  data: () => {
		return {
			messages: [],
			user: "Fulano",
			msg: "Ipsis Litteris",
			title: "Grupo random"
		}
	},
	methods: {
		add: function(){
			const time = new Date();

			this.messages.push(
				{ userName: this.user, 
					text: this.msg, 
					now: `${time.getHours()} : ${time.getMinutes()}` 
				});
		}
	}
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@600&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Open+Sans&display=swap');

#app {
  font-family: 'Montserrat', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	font-weight: 300;
	font-size: 0.9em;
}

#talkField, button {
	background-color: #041C32;;
	color: #ECB365;
}

header {
	background-color: #1a1b26; 
	display: flex;
	justify-content: space-around;
	align-items: baseline;
	padding: 2.5%;
}

h2 {
	font-family: 'Montserrat', Arial, sans-serif;
	font-weight: 600;
	margin-right: 25%;
}

form {
	display: flex;
	flex-direction: column;
	margin-top: 2vh;
	font-family: 'Open Sans', Arial, sans-serif;
	letter-spacing: 1%;
}

input {
	width: 50vw;
	margin-bottom: 1vh;
}

button { 
	display: flex;
	align-items: center;
	justify-content: space-evenly;
	width: 35vw;
	height: 7vh;
	border-radius: 10px;
	border: none;
}

ul {
	background-color: #041C32;
	padding: 0;
	padding: 5%;
}
</style>
