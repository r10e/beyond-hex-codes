<template>
	<color-picker v-bind="color" @input="hueInput"></color-picker>
	Hue: {{ color.hue }}
	<br />
	<label for="saturation">Saturation: {{ color.saturation }}% </label>
	<input
		id="saturation"
		type="range"
		min="0"
		max="100"
		value="100"
		@change="saturationChange"
	/>
	<br />
	<label for="lightness">Lightness: {{ color.luminosity }}% </label>
	<input
		id="lightness"
		type="range"
		min="0"
		max="100"
		value="100"
		@change="lightnessChange"
	/>
	<ColorBlock
		:color="`hsl(${color.hue}, ${color.saturation}%, ${color.luminosity}%)`"
		ratio="5 / 1"
	></ColorBlock>
</template>

<script setup lang="ts">
import { reactive } from 'vue';
import ColorPicker from '@radial-color-picker/vue-color-picker';
import ColorBlock from './ColorBlock.vue';

const color = reactive({
	hue: 50,
	saturation: 100,
	luminosity: 50,
	alpha: 1,
});

const hueInput = (hue: number) => (color.hue = hue);
const saturationChange = (event: Event) =>
	(color.saturation = (event.currentTarget as HTMLInputElement).valueAsNumber);
const lightnessChange = (event: Event) =>
	(color.luminosity = (event.currentTarget as HTMLInputElement).valueAsNumber);
</script>

<style>
@import '@radial-color-picker/vue-color-picker/dist/vue-color-picker.min.css';
</style>
