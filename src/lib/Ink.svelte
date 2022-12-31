<script lang="ts">
	import { browser } from '$app/environment';
	import ink, { type Instance, type Options } from 'ink-mde';
	import { onMount } from 'svelte';

	export let editor: Instance | undefined = undefined;
	export let options: Options | undefined = undefined;

	let divRef: HTMLDivElement;

	onMount(() => {
		editor = ink(divRef, options);
	});

	$: {
		if (browser && editor && options) {
			editor.reconfigure(options);
		}
	}
</script>

<div bind:this={divRef} />
