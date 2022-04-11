<template>
	<div id="talkField">
		<header>
			<font-awesome-icon icon="AngleLeft" />
			<h2>Grupo random</h2>
		</header>
  
		<ul>
			<MessageComponent v-for="message in messages" v-bind:key="message.msg" :msg="message" />
		</ul>
	</div>
	
	<form>
		<input v-model="user" placeholder="Nome do usuario" />
		<input v-model="msg" placeholder="Mensagem"/>
		
		<button v-on:click.prevent="add">Adicionar mensagem</button>
	</form>
</template>

<script>
import MessageComponent from './components/Message.vue';

export default {
  name: 'App',
	components: { MessageComponent },
  data: () => {
		return {
			messages: [{ userName: "Luigi", text: "Salve", now: "13:47" }],
			user: "",
			msg: ""
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

#app {
  font-family: 'Montserrat', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
	font-size: 0.9em;
}

#talkField {
	background-color: #041C32;;
	color: #ECB365;
}

header {
	background-color: #1a1b26; 
	display: flex;
	justify-content: center;
	padding: 2.5%;
}

form {
	display: flex;
	flex-direction: column;
	margin-top: 2vh;
}

input {
	width: 50vw;
	margin-bottom: 1vh;
}

button { width: 25vw; }

ul {
	background-color: #041C32;
	padding: 0;
	padding: 5%;
}
</style>
