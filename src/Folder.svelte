<script>
	export let isOpen = true;
	export let name = "default"

</script>

<div class="folder-container">
	<p on:click={() => isOpen = !isOpen}>{name}</p>
	<div class="folder" class:isOpen>
		<slot></slot> 
	</div>
</div>

<style>
	.folder-container {
		border: lightgray 2px solid;
		padding: 8px;
	}
	.folder {
		display: block;
		max-height: 0;
		overflow: hidden;
		box-shadow: 2px 2px 6px grey;
		transition: max-height 250ms;
	}
	.isOpen {
		max-height: 500px;
	}

</style>