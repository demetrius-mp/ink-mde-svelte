# ink-mde-svelte

> Svelte wrapper for the [ink-mde](https://github.com/voracious/ink-mde) component.

## Usage

```svelte
<script lang="ts">
 import { Ink } from 'ink-mde-svelte';
</script>

<Ink
 options={{
  interface: {
   toolbar: true
  }
 }}
/>

```

### You can bind to the `ink-mde` instance as follows

```svelte
<script lang="ts">
 import { Ink } from 'ink-mde-svelte';
 import type { Instance } from 'ink-mde';

 let editor: Instance;
</script>

<Ink
 bind:editor
 options={{
  interface: {
   toolbar: true
  }
 }}
/>
```

### You can apply styles to the `ink-mde` component as follows

```svelte
<script lang="ts">
  import { Ink } from 'ink-mde-svelte';
  import type { Instance } from 'ink-mde';
</script>

<Ink
 options={{
  interface: {
    toolbar: true
  }
 }}
/>

<!-- 
 apply styles using the `:global()` modifier, 
 and using the component selectors.
-->
<style>
 :global(.ͼ1.cm-editor.cm-focused) {
  outline: 0 !important;
 }

 :global(.ink-mde) {
  height: calc(100vh - 37px) !important;
 }
</style>
```

### Reactive options property

It is worth noting that the `options` property is reactive via `editor.reconfigure(options);`. This means that any change on the `options` property will cause the editor to be reconfigured.

```svelte
<script lang="ts">
 import { Ink } from 'ink-mde-svelte';

 let theme: 'light' | 'dark' = 'light';

 function toggleTheme() {
  theme = theme === 'dark' ? 'light' : 'dark';
 }
</script>

<button on:click={toggleTheme}>Toggle theme</button>

<Ink
 options={{
  interface: {
   toolbar: true,
   appearance: theme
  }
 }}
/>
```
