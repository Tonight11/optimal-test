<template>
	<div>
		<ul class="item-list">
			<li class="item" v-for="(item, index) in items" :key="index">
				<div class="item-tes">
					{{ item.name }} <br />
					{{ item.value }}
				</div>
				<div class="item-change" @click="$emit('selectItem', item)">
					change✏️
				</div>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		props: {
			items: {
				type: Array,
				required: true,
			},
		},
		emits: ['selectItem'],
	};
</script>

<style>
	.item-list {
		display: flex;
		flex-direction: column;

		gap: 20px;
	}
	.item {
		padding: 20px;
		color: white;
		flex: 1;
		border-radius: 8px;
		display: flex;
		justify-content: space-between;
		align-items: center;
		width: 100%;
		box-shadow: -4px -4px 5px #200441, 4px 4px 5px #000000;
		position: relative;
		background-color: #120722;
		font-size: 18px;
	}
	.item-change {
		cursor: pointer;
	}
</style>
