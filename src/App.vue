<template>
	<div class="flex items-center justify-center overflow-hidden min-h-screen bg-[#080710]">
		<div class="z-1 p-0.5 overflow-hidden rounded-[10px] relative w-[400px]" @mousemove="handleMouseMove" @mouseleave="hideCircle">
			<div class="circle -z-1" :style="{top: `${y - 200}px`, left: `${x - 200}px`, opacity: isCircleVisible ? 0.6 : 0}"></div>
			<div class="bg-black z-10 rounded-[10px]">
				<form
					@submit.prevent="SubmitEvent"
					class="overflow-hidden bg-white/10 z-10 relative p-[35px] pt-[50px] border border-white/10 rounded-[10px] shadow-[0_0_40px_rgba(0,0,0,0.5)] backdrop-blur text-white">
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
						<label class="block text-lg mb-2" for="email">Email</label>
						<input
							type="email"
							v-model="email"
							id="email"
							placeholder="email"
							required
							class="w-full h-[50px] bg-white/10 px-3 text-white placeholder:text-gray-300 rounded-[4px] focus:outline-none" />
					</div>
					<button type="submit" class="w-full py-4 mt-10 bg-white text-[#080710] rounded-[4px] font-bold text-lg">Log In</button>
				</form>
			</div>
		</div>
	</div>
	<ResultAlert v-if="submitted" :name="name" :email="email" />
</template>
<script>
import ResultAlert from "./components/ResultAlert.vue";
import {ref} from "vue";

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
		},
	},
	setup() {
		const x = ref(0);
		const y = ref(0);
		const isCircleVisible = ref(false);

		// تغییر مکان دایره با حرکت موس
		const handleMouseMove = (event) => {
			const rect = event.currentTarget.getBoundingClientRect();
			x.value = event.clientX - rect.left;
			y.value = event.clientY - rect.top;
			isCircleVisible.value = true;
		};

		// مخفی‌سازی دایره وقتی موس خارج شد
		const hideCircle = () => {
			isCircleVisible.value = false;
		};

		return {
			x,
			y,
			isCircleVisible,
			handleMouseMove,
			hideCircle,
		};
	},
};
</script>
