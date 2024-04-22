<script lang="ts">
	import BarChart from '$lib/components/BarChart.svelte';
	import LineChart from '$lib/components/LineChart.svelte';
	import Grid, { GridItem } from 'svelte-grid-extended';

	let components = [
		{
			name: 'LineChart',
			component: LineChart,
			x: 0,
			y: 0,
			w: 4,
			h: 5
		},
		{
			name: 'BarChart',
			component: BarChart,
			x: 4,
			y: 0,
			w: 4,
			h: 5
		}
	];
	const itemSize = { width: 100, height: 40 };

	function addLineChart() {
		components = [
			...components,
			{
				name: 'LineChart',
				component: LineChart,
				x: 0,
				y: 0,
				w: 4,
				h: 5
			}
		];
	}

	function addBarChart() {
		components = [
			...components,
			{
				name: 'BarChart',
				component: BarChart,
				x: 0,
				y: 0,
				w: 4,
				h: 5
			}
		];
	}
</script>

<div class="min-h-screen p-8">
	<div class="flex gap-2">
		<button class="btn" on:click={addLineChart}>Add Line Chart</button>
		<button class="btn" on:click={addBarChart}>Add Bar Chart</button>
	</div>

	<Grid {itemSize} cols={10} rows={10} class="mt-16 p-0" collision="compress">
		{#each components as component}
			<GridItem
				bind:x={component.x}
				bind:y={component.y}
				bind:w={component.w}
				bind:h={component.h}
				class="item"
			>
				<svelte:component this={component.component} />
			</GridItem>
		{/each}
	</Grid>
</div>
