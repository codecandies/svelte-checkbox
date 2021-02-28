<script>
	import { createEventDispatcher } from "svelte";
	export let name;
	export let checked;
	export let color = '#666';
	const dispatch = createEventDispatcher();
	
	const handleChange = () => {
		checked = !checked;
    dispatch( "change", checked );
  };
</script>

<style>
	.vhidden {
		clip: rect(0 0 0 0);
  	clip-path: inset(50%);
  	height: 1px;
  	overflow: hidden;
  	position: absolute;
  	white-space: nowrap;
  	width: 1px;
	}
	.Checkbox {
		background: #fff;
		border-radius: 4px;
		padding: 4px
	}
	label {
		align-items: center;
		display: flex;
	}
	span {
		color: #666;
		padding-left: 4px
	}
	svg {
		color: var(--svgcolor);
		flex: 0 0 24px;
	}
	input[type=checkbox] + .svg-checked,
	input[type=checkbox]:checked + .svg-checked + .svg-unchecked {
		display: none;
	}
	input[type=checkbox]:checked + .svg-checked,
	input[type=checkbox] + .svg-checked + .svg-unchecked {
		display: inline-block;
	}
</style>

<div class="Checkbox" style="--svgcolor: {color}">
	<label>
		<input type="checkbox" class="vhidden" {name} {checked} on:change={handleChange}>
		<svg class="svg-checked" aria-hidden="true" fill="none" height="24" width="24">	
			<rect fill="currentColor" height="16" rx="4" width="16" x="4" y="4"/><path clip-rule="evenodd" d="M16.84 7.6a.5.5 0 01.1.7l-5.006 6.674a1.8 1.8 0 01-2.06.604c-.241-.089-.46-.229-.642-.41l-2.586-2.585a.5.5 0 11.708-.708l2.583 2.584a.8.8 0 00.942.135c.1-.054.187-.13.255-.22L16.14 7.7a.5.5 0 01.7-.1z" fill="#fff" fill-rule="evenodd"/>
		</svg>
		<svg class="svg-unchecked" aria-hidden="true" fill="none" height="24" width="24">
			<rect height="16" rx="4" width="16" x="4" y="4"/><path clip-rule="evenodd" d="M16 5H8a3 3 0 00-3 3v8a3 3 0 003 3h8a3 3 0 003-3V8a3 3 0 00-3-3zM8 4a4 4 0 00-4 4v8a4 4 0 004 4h8a4 4 0 004-4V8a4 4 0 00-4-4H8z" fill="currentColor" fill-rule="evenodd"/>
		</svg>
		<span><slot></slot></span>
	</label>
</div>