<script lang="ts">
	import type { SvelteUINumberSize } from '$lib/styles';
	import { Meta, Template, Story } from '@storybook/addon-svelte-csf';
	import { ChipGroup } from '../index';

	const spacings: SvelteUINumberSize[] = ['xs', 'sm', 'md', 'lg', 'xl'];
	const directions: ('column' | 'row')[] = ['column', 'row'];

	let bindValue;
</script>

<Meta title="Components/Chip/ChipGroup" component={ChipGroup} />

<Template let:args>
	<ChipGroup {...args} />
</Template>

<Story
	name="ChipGroup"
	args={{
		items: [
			{ label: 'Chip', value: 'chip' },
			{ label: 'Dip', value: 'dip' }
		]
	}}
/>

<Story name="Allow multiple">
	<ChipGroup
		bind:value={bindValue}
		multiple
		items={[
			{ label: 'One', value: 'one' },
			{ label: 'Two', value: 'two' },
			{ label: 'Three', value: 'three' }
		]}
	/>
	<p>Variable bound to value: <code>{JSON.stringify(bindValue)}</code></p>
</Story>

<Story name="Bind value">
	<ChipGroup
		bind:value={bindValue}
		items={[
			{ label: 'One', value: 'one' },
			{ label: 'Two', value: 'two' },
			{ label: 'Three', value: 'three' }
		]}
	/>
	<p>Variable bound to value: <code>{JSON.stringify(bindValue)}</code></p>
</Story>

<Story name="Spacing">
	{#each spacings as spacing}
		<p>Spacing: {spacing}</p>
		<ChipGroup
			bind:value={bindValue}
			{spacing}
			items={[
				{ label: 'One', value: 'one' },
				{ label: 'Two', value: 'two' },
				{ label: 'Three', value: 'three' }
			]}
		/>
	{/each}
</Story>

<Story name="Directions">
	{#each directions as direction}
		<p>Direction: {direction}</p>
		<ChipGroup
			bind:value={bindValue}
			{direction}
			items={[
				{ label: 'One', value: 'one' },
				{ label: 'Two', value: 'two' },
				{ label: 'Three', value: 'three' }
			]}
		/>
	{/each}
</Story>

<Story name="Input label">
	<ChipGroup
		bind:value={bindValue}
		multiple
		label="Pick as many as you like"
		items={[
			{ label: 'One', value: 'one' },
			{ label: 'Two', value: 'two' },
			{ label: 'Three', value: 'three' }
		]}
	/>
</Story>
