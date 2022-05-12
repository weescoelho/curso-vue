<template>
	<div>
		<h1>Minha Lista de tarefas!</h1>

		<button @click="() => showList = !showList">Ver Lista</button>

<!-- Aplicação de diretivas -->

 <input type="" v-focus>

	<ul v-if="showList">
		<li v-for="(task, index) in tasks" :key="`${task}-${index}`">
			{{task.name}}
		</li>
	</ul>

	<p v-else>Lista escondida</p>

	</div>
</template>

<script>

const focus = {
	inserted: (el) => {
		el.focus()
	}
}


/*Semelhante ao useState, cada key do objeto dentro do data é um estado.*/

export default {
	directives:{
		focus
	},
	data:() => ({
		showList:false,
		tasks:[
			{name: 'Fazer o curso', isDone: false},
			{name: "Teste" , isDone: true}
		]
	})
}
</script>
