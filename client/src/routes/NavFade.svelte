<script lang="ts">
	export let title = 'title';
	export let subtitle = 'subtitle';
	export let index = 0;
	export const displace = 18;

	let percentages = Array.from({ length: displace }, (_, i) => 1.1 * (displace - i));
	let sum = percentages.reduce((a, b) => a + b, 0);
	percentages = percentages.map((p) => (p / sum) * 114);
	let result = percentages.map((p) => `calc(${p}% - .4rem)`).join(' ');

</script>

<div class="role">
	<div class="title">
		<p style="width: 100%;">{title}</p>
		<div class="fade" style="grid-template-columns: {result};">
			{#each Array.from({ length: displace }, (_, i) => i + 1) as index}
				<p style="transition-delay: {index * 10}ms;"></p>
			{/each}
		</div>
	</div>

	<div class="subtitle">
		<p style="transition-delay: {index * 10}ms;">[0{index}] {subtitle}</p>
        <!-- <span class="arrow"> -></span> -->
	</div>
</div>
