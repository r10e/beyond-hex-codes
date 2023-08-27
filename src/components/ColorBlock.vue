<template>
	<div class="block">
		<span class="caption">{{ color }}</span>
		<slot />
	</div>
</template>

<script setup lang="ts">
const props = withDefaults(defineProps<{ color: string; ratio?: string }>(), {
	ratio: '1 /1',
});
</script>
<style>
.block {
	display: grid;
	gap: 1rem;
	place-content: center;
	background: v-bind(color);
	border-radius: 5px;
	aspect-ratio: v-bind(ratio);
}
.caption {
	background-color: white;
	padding: 0.5rem;
	border-radius: 3px;
}
</style>
