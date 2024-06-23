<script>
	import '$lib/styles/style.scss';
	import Conway from './Conway.svelte';
	let bored = false;
</script>

<section>
	<div class="content">
		<p>
			Hi, I'm Amor Budiyanto. I'm a Year 13 High School student at Cashmere High School with passion
			in Computer Science.
		</p>
	</div>
	<div class="board {bored ? 'game' : ''}" on:click={() => (bored = true)}>
		{#if bored}
			<Conway></Conway>
		{:else}
			<p>bored?</p>
		{/if}
	</div>
</section>
