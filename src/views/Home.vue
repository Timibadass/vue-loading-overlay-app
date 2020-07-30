<template>
	<div class="home" ref="homeCont">
		<form @submit.prevent="logIn">
			<loading-overlay :active="isLoading" :is-full-page="fullPage" :loader="loader">
				<div class="loader__container"></div>
			</loading-overlay>
			<label for="name" class="label">Name</label>
			<input type="text" name="name" class="input__field" id="name" />
			<label for="email" class="label">Email Address</label>
			<input type="email" name="email" class="input__field" id="email" />
			<!-- replace existing button -->
			<form-button class="submit__button">Save</form-button>
		</form>
	</div>
</template>

<script>
	// import button component
	import FormButton from "@/components/button.vue";
	export default {
		name: "Home",
		data() {
			return {
				isLoading: false,
				fullPage: false,
				loader: "bars"
			};
		},
		components: {
			FormButton
		},
		methods: {
			logIn() {
				this.isLoading = true;
				setTimeout(() => {
					this.isLoading = false;
				}, 3000);
			}
		}
	};
</script>
<style scoped>
	.home {
		width: 500px;
		margin: auto;
		height: 500px;
		text-align: left;
	}

	form {
		width: 100%;
		max-width: 300px;
		margin: auto;
		/* important if you do not want fullscreen loader */
		position: relative;
	}

	@keyframes move {
		0%,
		50% {
			transform: translateY(50px);
		}

		50% {
			transform: rotate(90deg);
			transform: translateY(50px);
		}
		60% {
			transform: translateX(50px);
		}
		75% {
			rotate: 0;
		}
		100% {
			transform: translateX(0);
			transform: translateY(0);
		}
	}

	.loader__container {
		width: 20px;
		height: 100px;
		background-color: #000;
		animation: move 5s ease-in-out infinite alternate-reverse forwards;
	}

	.label {
		display: block;
		width: 100%;
		margin-bottom: 10px;
	}

	.input__field {
		margin-bottom: 10px;
		height: 40px;
		border: 1px solid #e4e4e4;
		border-radius: 5px;
		padding-left: 10px;
		width: 250px;
	}

	.submit__button {
		width: 80px;
		height: 40px;
		display: block;
		margin: 20px auto;
		background-color: #fff;
		border: 1px solid #e4e4e4;
		box-shadow: 1px 2px 4px 1px #e4e4e4;
	}
</style>
