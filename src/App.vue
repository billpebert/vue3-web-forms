<template>
	<SignUpForm />
</template>

<script>
	import SignUpForm from "./components/SignUpForm.vue";

	export default {
		name: "App",
		components: {
			SignUpForm,
		},
	};
</script>

<style>
	@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600&display=swap");
	* {
		font-family: "Poppins", sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}

	#app {
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}

	body {
		margin: 0;
    padding: 0 12px;
		background: #eee;
	}
</style>
