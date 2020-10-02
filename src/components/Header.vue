<template>
	<div>
		<nav class="nav">
			<h1>Roles</h1>
		</nav>
	</div>
</template>

<script>
export default {
	name: 'Header',
	data() {
		return {
			roles: ['Customer', 'Tech Lead', 'Mentor', 'Narrator', 'Teacher'],
			click: ''
		};
	}
};
</script>

<style scoped></style>
