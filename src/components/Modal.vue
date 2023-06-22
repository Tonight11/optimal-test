<script>
	export default {
		emits: ['closeModal'],
	};
</script>

<template>
	<div class="modal">
		<div class="modal__close" @click="$emit('closeModal')">X</div>
		<slot />
	</div>
</template>

<style scoped>
	.modal {
		background: rgba(38, 38, 38, 0.5);
		max-width: 250px;
		min-width: 250px;
		z-index: 100;
		/* Primary Border */
		backdrop-filter: blur(8px);
		position: absolute;
		top: 0;
		bottom: 0;
		right: 0;
	}

	.modal__close {
		position: absolute;
		top: 10px;
		right: 10px;
		cursor: pointer;
		z-index: 2;
	}
</style>
