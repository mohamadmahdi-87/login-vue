<template>
	<div
		@mouseenter="stopTimer"
		@mouseleave="resumeTimer"
		v-if="showAlert"
		:class="alertClass"
		class="fixed flex items-center max-w-110 gap-7 top-5 p-6 bg-neutral-600 border-r-4 border-green-600 text-white rounded-l-md shadow-lg transition-all duration-500 ease-out">
		<div @click="hideAlert" class="transition-all group hover:text-red-500 flex place-content-center">
			<span class="w-10 h-10 flex justify-center items-center bg-neutral-800 rounded-full">
				<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="group-hover:scale-[1.1] size-7">
					<path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12" />
				</svg>
			</span>
		</div>
		<div>
			<p>
				<strong>Name:</strong>
				{{ name }}
			</p>
			<p>
				<strong>Email:</strong>
				{{ email }}
			</p>
		</div>
	</div>
</template>

<script>
export default {
	props: ["name", "email"],
	data() {
		return {
			showAlert: true,
			alertClass: "translate-x-full right-0",
			isTiming: null,
		};
	},
	mounted() {
		this.timing();
	},
	methods: {
		timing() {
			setTimeout(() => {
				this.alertClass = "translate-x-0 right-6";
			}, 50);

			this.isTiming = setTimeout(() => {
				this.hideAlert();
			}, 2500);
		},
		stopTimer() {
			clearTimeout(this.isTiming);
		},

		resumeTimer() {
			this.isTiming = setTimeout(() => {
				this.hideAlert();
			}, 2500);
		},
		hideAlert() {
			this.alertClass = "translate-x-full right-0";
		},
	},
};
</script>
