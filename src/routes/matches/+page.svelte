<script>
    let team1 = '';
    let team2 = '';
    /**
	 * @type {string | any[]}
	 */
    let matches = [];

    async function fetchMatches() {
        // Replace with your actual API endpoint
        const response = await fetch(`/api/matches?team1=${team1}&team2=${team2}`);
        matches = await response.json();
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
    <h1>Match Lookup</h1>
    <div>
        <label>
            Team 1:
            <input type="text" bind:value={team1} />
        </label>
    </div>
    <div>
        <label>
            Team 2:
            <input type="text" bind:value={team2} />
        </label>
    </div>
    <button on:click={fetchMatches}>Search</button>

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