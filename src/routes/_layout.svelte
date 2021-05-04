<script>
	import Nav from '../components/Nav.svelte';

	export let segment;
</script>

<style>
	main {
		/*position: relative;*/
		/*max-width: 56em;*/
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
		display: flex;
		justify-content: center;
		flex-direction: column;
		align-items: center;
	}
	footer{
		display: flex;
		position: relative;
		align-items: center;
		justify-content: center;
		bottom: 0;
	}
	footer>p{
		font-size: 1.6rem;
	}
</style>

<Nav {segment}/>

<main>
	<slot></slot>
</main>
<footer>
	<p>Derechos Reservados &copy; 2021 MovieView.com por Christian Vilca Apaza</p>
</footer>