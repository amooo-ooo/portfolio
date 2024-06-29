<script lang="ts">
	import { onMount } from 'svelte';
	import cat_1 from '$lib/images/cats/cat (1).png';
	import cat_2 from '$lib/images/cats/cat (2).png';
	import cat_3 from '$lib/images/cats/cat (3).png';
	import cat_4 from '$lib/images/cats/cat (4).png';
	import cat_5 from '$lib/images/cats/cat (5).png';
	import cat_6 from '$lib/images/cats/cat (6).png';
	import cat_7 from '$lib/images/cats/cat (7).png';
	import cat_8 from '$lib/images/cats/cat (8).png';
	import cat_9 from '$lib/images/cats/cat (9).png';
	import cat_10 from '$lib/images/cats/cat (10).png';
    import cat_11 from '$lib/images/cats/cat (11).png';
	import cat_14 from '$lib/images/cats/cat (14).png';

	let cats = [cat_1, cat_2, cat_3, cat_4, cat_5, cat_6, cat_7, cat_8, cat_9, cat_10, cat_11, cat_14];
	let images;
	let globalIndex = 0;
	let last = { x: 0, y: 0 };
	let limit = 34;

	const activate = (image, x, y, dx, dy) => {
		// Generate a random rotation degree between 0 and 360
		const rotation = Math.floor(Math.random() * 40) - 20;
		const size = Math.floor(Math.random() * 8 + 18);

		// Set the initial position to the current cursor position
		image.style.left = `${x}px`;
		image.style.top = `${y}px`;

		// After a short delay, update the position to the new position
		setTimeout(() => {
			image.style.left = `${x + dx * 0.1}px`;
			image.style.top = `${y + dy * 0.1}px`;
		}, 50);

		image.style.zIndex = globalIndex;
		image.style.transform = `translate(-50%, -50%) rotate(${rotation}deg)`;
		image.style.width = `${size}vmin`;
		image.style.zIndex = globalIndex % 50;

		image.dataset.status = 'active';

		last = { x, y };
	};

	const distanceFromLast = (x, y) => {
		return Math.hypot(x - last.x, y - last.y);
	};

	const handleOnMove = (e) => {
	// Calculate the top limit in pixels
	const topLimitPx = window.innerHeight * (limit / 100);
	// Calculate the bottom limit in pixels
	const bottomLimitPx = window.innerHeight * ((100 - 16) / 100); // 10vh from the bottom

	// Check if the cursor is below the top limit and above the bottom limit
	if (e.clientY > topLimitPx && e.clientY < bottomLimitPx) {
		if (distanceFromLast(e.clientX, e.clientY) > window.innerWidth / 12) {
			const lead = images[globalIndex % images.length],
				tail = images[(globalIndex - 6) % images.length];

			// Calculate dx and dy
			const dx = e.clientX - last.x;
			const dy = e.clientY - last.y;

			activate(lead, e.clientX, e.clientY, dx, dy);

			if (tail) tail.dataset.status = 'inactive';

			globalIndex++;
		}
	}
};


	onMount(() => {
		images = document.getElementsByClassName('image');
		window.onmousemove = (e) => handleOnMove(e);
		window.ontouchmove = (e) => handleOnMove(e.touches[0]);
	});
</script>

<div class="cats">
	{#each cats as src, i}
	<img class="image" data-index={i} data-status="inactive" {src} />
{/each}
</div>

<style>
	div.cats {
		height: 100vh;
		width: 100vw;
		margin: 0px;
		position: absolute;
		top: 0;
		left: 0;
		overflow-x: hidden;
		pointer-events: none;
	}

	.image {
		width: 40vmin;  
        max-height: 26vmin;
        object-fit: contain;
		position: absolute;
		transform: translate(-50%, -50%);
		transition:
			left 0.5s ease-out,
			top 0.5s ease-out;
	}

	.image[data-status='inactive'] {
		display: none;
	}

	.image[data-status='active'] {
		display: block;
	}
</style>
