<script>
	import Checkbox from './Checkbox.svelte'
	let checked = true;
	
	function handleChange({ detail }) {
    console.log("checked", detail);
  }
</script>

<style>
	.container {
		align-items: center;
		background: #ccc;
		display: flex;
		justify-content: center;
		margin: 0;
		min-height: 100%;
	}
</style>

<div class="container">
	<Checkbox name={'subscribe'} color={'#ff3e00'} bind:checked on:change="{handleChange}">
		Yes, I want that fancy newsletter thingy.
	</Checkbox>
</div>
