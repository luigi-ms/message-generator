<template>
	<li>
		<h3>{{ msg.userName }}</h3>
		<p id="text">{{ msg.text }}</p>
		<p id="time">
			<i class="fa-solid fa-check"></i>
			{{ msg.now }}
		</p>
	</li>
</template>

<script>
export default {
  name: 'MessageComponent',
  props: { msg: Object }
}
</script>

<style scoped>
	* {
		font-size: inherit;
	}

	li {
		display: flex;
		flex-direction: column;
		padding: 0.2% 2.5% 1% 2.5%;
		border: 1px dotted #ECB365;
		list-style: none;
		margin-bottom: 2%;
	}
	
	p {
		margin: 0;	
	}

	#time {
		align-self: end;
	}
</style>
