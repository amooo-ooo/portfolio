<script>
	import '$lib/styles/nav.scss';
	import Works from './Works.svelte';
</script>

<nav>
	<div class="corner">
		<p>amor</p>
	</div>

	<div class="main">
		<div class="controls">
			<div>
				<p>Home</p>
				<p>Work[14]</p>
			</div>
	
			<div>
				<p>About</p>
				<p>Contact</p>
			</div>
		</div>
		<Works></Works>
	</div>

	<div class="corner">
		<p>GMT+13 Local time</p>
		<p>12:00</p>
	</div>
</nav>