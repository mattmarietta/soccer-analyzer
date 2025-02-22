<script lang="ts">
    import { onMount } from "svelte";
    import { page } from "$app/state"; 
    import { writable } from "svelte/store";
    import { goto } from "$app/navigation";
    import ListItem from "../../../components/ListItem.svelte"; 

    interface Player {
        player: {
            id: number;
            name: string;
            photo: string;
            nationality: string;
        };
    }

    let players = writable<Player[]>([]);

    // Get team ID from the URL
    const teamID = page.params.teamID;

    // Function to fetch all players using pagination
    async function fetchPlayers(pageNumber = 1, accumulatedPlayers: Player[] = []) {
        if (!teamID) return;

        const response = await fetch(`https://v3.football.api-sports.io/players?team=${teamID}&season=2024&page=${pageNumber}`, {
            method: 'GET',
            headers: { 'x-rapidapi-key': '''' }
        });

        const data = await response.json();
        const newPlayers = data.response || [];
        const totalPages = data.paging?.total || 1; // Get total pages

        // Combine new players with accumulated ones
        const updatedPlayers = [...accumulatedPlayers, ...newPlayers];

        if (pageNumber < totalPages) {
            // Fetch next page recursively
            return fetchPlayers(pageNumber + 1, updatedPlayers);
        } else {
            // When all pages are fetched, update the store
            players.set(updatedPlayers);
        }
    }

    // Fetch players on mount
    onMount(() => {
        fetchPlayers();
    });

    function handlePlayerSelect(event: CustomEvent) {
        const playerID = event.detail.id;
        goto(`/matches/${playerID}`);
    }
</script>

<h1>Players for Team: {teamID}</h1>
<div class="overflow-y-auto grid grid-cols-3 gap-2">
    {#each $players as player}
        <ListItem
            itemID={player.player.id} 
            title={player.player.name}
            body={player.player.nationality}
            imgUrl={player.player.photo}
            on:select={handlePlayerSelect}
        />
    {/each}
</div>