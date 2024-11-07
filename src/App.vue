<template>
	<div class="flex items-center justify-center overflow-hidden min-h-screen bg-[#080710]">
		<div class="z-1 relative w-[400px]">
			<div class="absolute top-[-80px] left-[-80px] w-[200px] h-[200px] rounded-full bg-gradient-to-r from-[#0D47A1] to-[#42A5F5] z-[-1]"></div>
			<div class="absolute bottom-[-90px] right-[-60px] w-[200px] h-[200px] rounded-full bg-gradient-to-r from-[#E65100] to-[#FFA726] z-[-1]"></div>

			<form @submit.prevent="SubmitEvent" action="#" class="bg-white/10 p-[35px] pt-[50px] border border-white/10 rounded-[10px] shadow-[0_0_40px_rgba(0,0,0,0.5)] backdrop-blur text-white">
				<h2 class="text-4xl text-center mb-8 font-semibold">Login Here</h2>

				<div class="mb-6">
					<label class="block text-lg mb-2" for="username">Username</label>
					<input
						type="text"
						v-model="name"
						id="username"
						placeholder="username"
						required
						class="w-full h-[50px] bg-white/10 px-3 text-white placeholder:text-gray-300 rounded-[4px] focus:outline-none" />
				</div>

				<div class="mb-6">
					<label class="block text-lg mb-2" for="email">email</label>
					<input
						type="email"
						v-model="email"
						id="email"
						placeholder="email"
						required
						class="w-full h-[50px] bg-white/10 px-3 text-white placeholder:text-gray-300 rounded-[4px] focus:outline-none" />
				</div>

				<button type="submit" class="w-full py-4 mt-10 bg-white text-[#080710] rounded-[4px] font-bold text-lg">Log In</button>
				<ResultAlert v-if="submitted" :name="name" :email="email" />
			</form>
		</div>
	</div>
</template>

<script>
import ResultAlert from "./components/ResultAlert.vue";

export default {
	components: {
		ResultAlert,
	},
	data() {
		return {
			name: "",
			email: "",
			submitted: false,
		};
	},
	methods: {
		SubmitEvent() {
			this.submitted = true;
			console.log("submitted");
		},
	},
};
</script>
