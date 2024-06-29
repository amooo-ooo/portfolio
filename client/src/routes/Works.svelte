<script lang="ts">
	import NavFade from './NavFade.svelte';

	export const field = 'roles';

	const infos = {
		roles: [
			{ title: 'Volunteer Youth Leader', subtitle: 'New Zealand National Refugee Youth Coucil', year: '2024', url: 'https://www.linkedin.com/company/new-zealand-national-refugee-youth-council' },
			{ title: 'Volunteer Youth Advisor', subtitle: 'NZ Mental Health Foundation', year: '2024', url: 'https://mentalhealth.org.nz/'}, 
			{ title: 'Chief Technology Officer', subtitle: 'Ōtautahi Charity Ball', year: '2024', url: 'https://charityballchch.org/'},
			{ title: 'Digital Technologies Student Prefect', subtitle: 'Cashmere High School', year: '2024', url: 'https://www.cashmere.school.nz/' },
			{ title: 'Computer Science STAR Student', subtitle: 'University of Canterbury', year: '2024', url: 'https://www.canterbury.ac.nz/study/academic-study/engineering/schools-and-departments-engineering-forestry-product-design/computer-science-and-software-engineering-department/study-with-csse/computer-science-star-course' },
			{ title: 'Full Stack Developer', subtitle: 'Self-Employed', year: '2022', url: 'https://amorb.pages.dev/' }
		],
		projects: [
			{ title: 'Charity Website', subtitle: 'Hoon Hay Foodbank' },
			{ title: 'Selectify', subtitle: 'Ōtautahi Charity Ball' },
			{ title: 'PEP8PLUS', subtitle: 'Opensource Project' },
			{ title: 'Charity Website', subtitle: 'Ōtautahi Charity Ball' }
		]
	};
</script>

<div class="main">
	<div class="controls">
		<div>
			<p>Home</p>
			<p>Roles[{infos[field].length}]</p>
		</div>

		<div>
			<p>About</p>
			<p>Contact</p>
		</div>
	</div>
	<div class="roles">
		{#each infos[field] as role, index}
			<NavFade title={role.title} subtitle={role.subtitle} url={role.url} {index} />
		{/each}
	</div>
</div>
