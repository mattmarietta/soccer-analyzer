<script lang="ts">
    import { onMount } from "svelte";
    import { page } from "$app/stores"; 
    import { writable } from "svelte/store";
    import { goto } from "$app/navigation";
    import {get} from 'svelte/store';
    import ListItem from "../../../components/ListItem.svelte"; 


    interface Team {
        team: {
            id: number;
            name: string;
            logo: string;
            country: string;
        };
    }

    let teams = writable<Team[]>([]);
    let leagueID: string = "";

    // Get league ID from the URL
    $page.subscribe(($p) => {
        leagueID = $p.params.leagueID;
    });

    // Fetch teams for the selected league
    onMount(async () => {
        if (!leagueID) return;

        const response = await fetch(`https://v3.football.api-sports.io/teams?league=${leagueID}&season=2023`, {
            method: 'GET',
            headers: { 'x-rapidapi-key': 'b6c2d05fc1ed96232d51e735dcbea82c' }
        });

        const data = await response.json();
        teams.set(data.response || []);
    });

    function handleTeamSelect(event: CustomEvent) {
        const teamID = event.detail.id;
        goto(`/players/${teamID}`);
    }
</script>

<h1>Teams for League {leagueID}</h1>
<div class="grid grid-cols-3 gap-2">
    {#each $teams as team}
        <ListItem 
            title={team.team.name}
            body={team.team.country}
            imgUrl={team.team.logo}
            on:select={handleTeamSelect}
        />
    {/each}
</div>
