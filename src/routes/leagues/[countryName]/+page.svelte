
<script lang="ts">
    import ListItem from "../../../components/ListItem.svelte";
	import { onMount } from "svelte";
	import {writable} from "svelte/store";
	import { goto } from "$app/navigation";
	import { page } from "$app/state";
	let leagues = writable([]);



	const countryName = page.params.countryName;
	
	onMount(async () => {
		const response = await fetch(`https://v3.football.api-sports.io/leagues?type=League&country=${countryName}`, {
			method: 'GET',
			headers: { 'x-rapidapi-key': '''' }
		});
		const data = await response.json();
		//Update the leagues with the data from the API
		leagues.set(data.response);
	});


	function handleLeagueSelect(event){
		const leagueID = event.detail.id;
		//Navigate to the teams page with the league ID being passed as a parameter
		goto(`/teams/${leagueID}`);
	}
	 
</script>
<h1>Select a League</h1>
<div class="overflow-y-auto grid grid-cols-3 gap-2 ">
	{#each $leagues as league}
		<ListItem 
		title="{league.league.name}" 
		body="{league.league.type}" 
		imgUrl="{league.league.logo}"
		itemID = "{league.league.id}"
		on:select={handleLeagueSelect}
		/>
	{/each}
</div>
