<script lang="ts">
	import '../app.css';
	let { children } = $props();
</script>

<nav class="bg-gray-800 p-4">
    <ul class="flex justify-center space-x-4">
        <li><a href="/" class="text-white">Home</a></li>
        <li><a href="/players" class="text-white">Players</a></li>
        <li><a href="/teams" class="text-white">Teams</a></li>
        <li><a href="/matches" class="text-white">Matches</a></li>
        <li><a href="/about" class="text-white">About</a></li>
    </ul>
</nav>

{@render children()}


<style>
	main {
		background: green;
	}
</style>
