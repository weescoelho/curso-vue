<template>
	<div>
		<h1>Minha Lista de tarefas!</h1>

		<button @click="handleShowList">Ver Lista</button>

<!-- Aplicação de diretivas -->

 <input type="text" v-focus @keyup.enter="addTask" v-model="currentTask">

	<ul v-if="showList">
		<li v-for="(task, index) in tasks" 
			:key="`${task}-${index}`" 
			@dblclick="complete(task)" 
			:class="{
				'line-through': task.isDone
				}"
			>
			{{task.name}}
			<button @click="remove(task)">&times;</button>
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
		currentTask : '',
		showList:false,
		tasks:[
			{name: 'Fazer o curso', isDone: false},
			{name: "Teste" , isDone: true}
		]
	}),
	methods:{
		addTask: (task) => {
			this.tasks.push({
				name: this.currentTask,
				isDone:false,
			})
			this.currentTask = ''
		},
		complete:(task) => {
			this.tasks = this.tasks.filter(t => {
				if(t.name === task.name){
					return {...t, isDone: !t.isDone}
				}
				return {...t}
			})
		},
		remove: (task) => {
			this.tasks = this.tasks.filter(t => t.name !== task.name)
		},
		handleShowList: () => {
			this.showList = !this.showList
		}
	}
}
</script>

<style scoped>
.line-through {
	text-decoration: line-through;
}
</style>

