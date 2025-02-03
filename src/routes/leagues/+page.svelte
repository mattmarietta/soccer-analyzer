
<script lan="ts">
    import ListItem from "../../components/ListItem.svelte";
	import { onMount } from "svelte";
	let leagues = [];
	
  async function fetchData() {
		const response = await fetch("https://v3.football.api-sports.io/leagues?type=League&country=England", {
			method: 'GET',
			headers: {
				'x-rapidapi-key': 'b6c2d05fc1ed96232d51e735dcbea82c'
			}
		});
		leagues = await response.json()
	};
	 
	onMount(fetchData);
</script>
<h1>Select a League</h1>
<div class="overflow-y-auto grid grid-cols-3 gap-2 ">
{#each leagues.response as league}
	<ListItem title="{league.league.name}" body="{league.league.type}" imgUrl="{league.league.logo}" />
{/each}
</div>