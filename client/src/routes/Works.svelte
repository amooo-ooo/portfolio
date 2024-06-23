<script>
	import NavFade from './NavFade.svelte';

	export const field = 'roles';

	const infos = {
		roles: [
			{
				title: 'Digital Technologies Student Prefect',
				subtitle: 'Cashmere High School',
				year: '2024'
			},
			{ title: 'UC STAR Student', subtitle: 'University of Canterbury', year: '2024' },
			{
				title: 'Youth Leader',
				subtitle: 'New Zealand National Refugee Youth Coucil',
				year: '2024'
			},
			{ title: 'Chief Technology Officer', subtitle: 'Ōtautahi Charity Ball', year: '2024' },
			{ title: 'Full Stack Developer', subtitle: 'Self-Employed', year: '2022' }
		],
        projects: [
            {title: "Charity Website", subtitle: "Hoon Hay Foodbank"},
            {title: "Selectify", subtitle: "Ōtautahi Charity Ball"},
            {title: "PEP8PLUS", subtitle: "Opensource Project"}, 
            {title: "Charity Website", subtitle: "Ōtautahi Charity Ball"},
        ]
	};
</script>

<div class="main">
	<div class="controls">
		<div>
			<p>Home</p>
			<p>Who am I?[{infos[field].length}]</p>
		</div>

		<div>
			<p>About</p>
			<p>Contact</p>
		</div>
	</div>
	<div class="roles">
		{#each infos[field] as role, index}
			<NavFade title={role.title} subtitle={role.subtitle} {index} />
		{/each}
	</div>
</div>
