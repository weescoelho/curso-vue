<template>
	<h1 v-bind:style="{textDecoration: decoration}">Hello World! , {{ name }}</h1>
	<input type="text" v-model="name"/>

	<br/>

	<a :href="link">Link pro curso!</a>

</template>

<script>
export default {
	data: () => ({
		name: 'Weslley',
		decoration:'underline',
		link:'http://google.com.br'
	})
}
</script>

<style scoped>

</style>
