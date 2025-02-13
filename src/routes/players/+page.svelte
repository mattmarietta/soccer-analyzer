<script lang="ts">
    import { onMount } from "svelte";
    import { page } from "$app/stores"; 
    import { goto } from "$app/navigation";
    import { writable } from "svelte/store";

    let players = writable([]);
    let teamID;

    onMount(async () => {
        teamID = $page.params.teamID;
        const response = await fetch(`https://v3.football.api-sports.io/players?team=${teamID}&season=2023`, {
            method: 'GET',
            headers: { 'x-rapidapi-key': 'b6c2d05fc1ed96232d51e735dcbea82c' }
        });
        const data = await response.json();
        players = data.response;
    });
</script>

<h1>Players List</h1>
<div class="grid grid-cols-3 gap-2">
    {#each players as player}
        <div class="p-4 bg-white shadow-md rounded-lg">
            <img src="{player.player.photo}" alt="{player.player.name}" class="w-20 h-20 mx-auto"/>
            <h2 class="text-lg font-bold">{player.player.name}</h2>
            <p>Age: {player.player.age}</p>
            <p>Position: {player.statistics[0].games.position}</p>
        </div>
    {/each}
</div>