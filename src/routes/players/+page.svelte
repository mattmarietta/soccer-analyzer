<script>


let playerStats = null;
let season = '';
let player = '';
let matches = [];

async function fetchPlayer() {
    const response = await fetch(`/api/players?player=${player}&season=${season}`);
    playerStats = await response.json();
    matches = playerStats.matches;
}

</script>


<style>
    .matches-container {
        padding: 20px;
    }
    .match {
        margin-bottom: 10px;
    }
</style>

<div class="matches-container">
    <h1>Player Lookup</h1>
    <div>
        <label>
            Player:
            <input type="text" bind:value={player} />
        </label>
    </div>
    <button on:click={fetchPlayer}>Search</button>

    {#if matches.length > 0}
        <h2>Matches</h2>
        {#each matches as match}
            <div class="match">
                <p>{match.date}: {match.team1} vs {match.team2} - {match.score}</p>
            </div>
        {/each}
    {:else}
        <p>No matches found</p>
    {/if}
</div>