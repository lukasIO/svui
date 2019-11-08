<script>
	import Svui from './Svui.svelte';
	import Folder from './Folder.svelte';
	
	let sliderValue = 0;
	let textValue = "test";
	let boolValue = false;
	
	let arrayValue = "horseradish";
	let optionArray = ["cucumber", "horseradish", "artichokes"];
	
	let objectValue = 1;
	let optionObject = {"soup": 0, "pasta": 1, "pizza": 2};

	$: console.log(sliderValue);
	$: console.log(boolValue);
	$: console.log(textValue);
	$: console.log(arrayValue);
	$: console.log(objectValue);
	
	function triggerFunction() {
		console.log("function triggered");
		console.log(sliderValue, boolValue, textValue);
	}
	
</script>

<h1>Hello UI</h1>


<div class="ui-container">
	<Folder name="slider and text">
		<Svui bind:value={sliderValue} min="-20" max="5" label="myslider"/>
		<Svui bind:value={textValue} label="mytext"/>
	</Folder>
	<Folder name="bool and trigger" isOpen={false}>
		<Svui bind:value={boolValue} label="mybool"/>
		<Svui bind:value={triggerFunction} label="myTrigger"/>
	</Folder>
	<Folder name="arrays" isOpen={false}>
		<Svui bind:value={arrayValue} bind:options={optionArray} label="myArray"/>
		<Svui bind:value={objectValue} bind:options={optionObject} label="myArray"/>
	</Folder>
</div>

<style>
	.ui-container {
		width: 300px;
	}
	
</style>





