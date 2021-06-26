<script lang="ts">
	import PalletGenerator from './views/PalletGenerator.svelte';
	import Contrast from './views/Contrast.svelte';

	let selectedTab = PalletGenerator;

	let tabs = {
		'pallet': PalletGenerator,
		'contrast': Contrast
	}

	function setTab(e) {
		selectedTab = tabs[e.target.value];
	}
</script>

<main>
	<form on:change={setTab}>
		<label>
			<input type="radio" name="tab" value="pallet" checked>
			<span>Pallet Generator</span>
		</label>
		<label>
			<input type="radio" name="tab" value="contrast">
			<span>Contrast</span>
		</label>
	</form>
	<div id="tab-container">
		<svelte:component this={selectedTab}/>
	</div>
</main>

<style>
	main {
		width: 100%;
		height: 100vh;
		display: grid;
		grid-template-rows: 60px 1fr;
	}

	form {
		display: grid;
		grid-template-columns: 1fr;
		grid-auto-columns: 1fr;
		grid-auto-flow: column;
		background-color: white;
		column-gap: 2px;
	}

	label {
		position: relative;
		width: 100%;
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 1.5em;
		font-weight: 700;
	}

	label > span {
		width: 100%;
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		box-sizing: border-box;
		background-color: #161616;
		margin-top: -3px;
		color: #494949;
	}

	input {
		position: absolute;
		visibility: none;
		width: 0;
		height: 0;
	}

	input:checked ~ span {
		margin-top: 0;
		color: white;
		background-color: #222;
	}
</style>