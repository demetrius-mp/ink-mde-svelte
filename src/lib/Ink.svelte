<script lang="ts">
	import ink, { type Instance, type Options } from 'ink-mde';
	import { onMount } from 'svelte';

	export let editor: Instance | undefined = undefined;
	export let options: Options | undefined = undefined;

	let divRef: HTMLDivElement;

	onMount(() => {
		editor = ink(divRef, options);
	});

	$: {
		if (editor && options) {
			editor.reconfigure(options);
		}
	}
</script>

<div bind:this={divRef} />
