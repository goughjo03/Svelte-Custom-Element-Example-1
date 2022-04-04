<svelte:options tag="mu-custom-incrementer" />

<script>
	import { count } from "./stores.ts";

	function increment() {
		// TODO increment the count
		count.update((n) => n + 1);
	}
</script>

<main>
	<button on:click={increment}> Increment + </button>
</main>
