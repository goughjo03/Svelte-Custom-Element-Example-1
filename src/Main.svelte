<svelte:options tag="my-custom-element" />

<script lang="ts">
	import { count } from './components/stores.js';
	let countValue: number
	count.subscribe(value => {
		countValue = value;
	});
	import Incrementer from "./components/Incrementer.svelte";
	export let name: string;
	export let id: string;

	function triggerEvent() {
		this.dispatchEvent(
			new CustomEvent("my-custom-event", { composed: true, detail: countValue })
		);
	}
</script>

<main id={id}>
	<h1>Hello {name}!</h1>
	<p>{countValue}</p>
	<Incrementer />
	<button on:click={triggerEvent}>Custom Event With Counter Value</button>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
