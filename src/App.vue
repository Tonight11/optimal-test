<template>
	<div>
		<item :items="items" @select-item="selectItem"></item>
		<Transition name="modal">
			<Modal
				@close-modal="selectedItem = false"
				v-if="selectedItem"
				teleport="body"
			>
				<form class="form" action="#" @submit.prevent="updateNewTask">
					<input type="text" v-model="editingText" />
					<button type="submit">Обновить</button>
				</form>
			</Modal>
		</Transition>
	</div>
</template>

<script>
	import Item from './components/Item.vue';
	import Modal from './components/Modal.vue';
	import { mapState, mapActions } from 'pinia';
	import { useItemsStore } from '@/store';

	export default {
		components: {
			Item,
			Modal,
		},
		data() {
			return {
				selectedItem: null,
				editingText: '',
			};
		},
		computed: {
			...mapState(useItemsStore, ['items']),
		},
		methods: {
			...mapActions(useItemsStore, ['updateTask']),
			selectItem(item) {
				this.selectedItem = item;
				this.editingText = item.value;
			},
			updateNewTask() {
				this.updateTask({
					name: this.selectedItem.name,
					value: this.editingText,
				});
				this.selectedItem = null;
			},
		},
	};
</script>

<style>
	.modal-enter-active,
	.modal-leave-active {
		transition: all 0.5s ease;
	}

	.modal-enter-from,
	.modal-leave-to {
		transform: translateX(100px);
		opacity: 0;
	}
</style>
