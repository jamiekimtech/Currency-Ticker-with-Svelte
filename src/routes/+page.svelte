<script>
	import { onMount } from 'svelte';

	let exchangeRate = '';

	onMount(async () => {
		try {
			const response = await fetch('https://api.exchangerate.host/latest?base=USD');
			const data = await response.json();
			exchangeRate = data.rates.KRW.toFixed(2);
		} catch (error) {
			console.log(error);
		}
	});
</script>

<main>
	<div>
		<h1>USD/KRW</h1>
		<h2>{exchangeRate}</h2>
	</div>
</main>

<style>
	:global(html, body) {
		height: 100%;
		margin: 0;
		padding: 0;
		overflow: hidden;
	}

	main {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100%;
		background-color: rgb(0, 0, 0);
		overflow: hidden;
	}

	h1 {
		font-size: 25px;
		margin: 0;
	}

	div {
		font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
		height: 3rem;
		width: 20rem;
		padding: 0.4rem;
		border: 2px solid antiquewhite;
		border-radius: 15px;
		display: flex;
		justify-content: space-between;
		align-items: center;
		color: antiquewhite;
		background-color: transparent;
	}
</style>
