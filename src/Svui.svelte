<script>
	
	import {onMount} from 'svelte';
	export let label = "";
	export let value;
	export let min = 0;
	export let max = 1;
	export let options;
	let type;

	onMount(() => {
		type = typeof value;
		console.log(type)
	});
	
	
</script>

<div class="ui-element">
{#if label != null && label != ""}
	<label>{label}</label>
{/if}
{#if (type == "string" || type == "number") && options}
	<select bind:value={value}>
		{#if Array.isArray(options)}
			{#each options as option}	
				<option value={option}>{option}</option>
			{/each}
		{:else}
			{#each Object.keys(options) as option}	
				<option value={options[option]}>{option}</option>
			{/each}
		{/if}		
	</select>		
{:else if (type == "string" && !options)}
	<input bind:value={value} />
{:else if (type == "boolean")}
	<input type="checkbox" bind:checked={value} />
{:else if (type == "function")}
	<button on:click={value}/>
{:else if (type == "number")}
	<input type="range" min={min} max={max} bind:value={value} step="0.01"/> 
	<p>{value}</p>
{/if}
</div>


<style>
	.ui-element {
		display: block;
		border: 1px grey solid;
		padding: 10px;
		width: 100%;
	}
	label {
		margin-bottom: 8px;
		max-width: 100%;
	}
	p {
		display: inline;
		margin-left: 8px;
	}
	
	input {
		display: inline;
		max-width: 100%;
	}
</style>

