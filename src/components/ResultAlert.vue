<template>
	<div v-if="showAlert" class="fixed top-5 p-6 bg-neutral-600 border-r-4 border-green-600 text-white rounded-l-md shadow-lg transition-all duration-500 ease-out" :class="alertClass">
		<p>
			<strong>Name:</strong>
			{{ name }}
		</p>
		<p>
			<strong>Email:</strong>
			{{ email }}
		</p>
	</div>
</template>

<script>
export default {
	props: ["name", "email"],
	data() {
		return {
			showAlert: true,
			alertClass: "translate-x-full right-0",
		};
	},
	mounted() {
		setTimeout(() => {
			this.alertClass = "translate-x-0 right-6";
		}, 50);
		setTimeout(() => {
			this.alertClass = "translate-x-full right-0";
		}, 2500);
	},
};
</script>
