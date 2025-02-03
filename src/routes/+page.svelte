<script>
    // Add any page-specific logic here if needed
</script>

<main class="flex flex-col items-center justify-center text-white">
    <h1 class="text-4xl font-bold mb-4 text-center">
        Welcome to <span class="text-green-400">Soccer Analyzer</span>
    </h1>
    <p class="text-lg mb-8 text-gra
    y-300 text-center max-w-prose">
        Analyze youfsdfsr favorite player, team performance, and match outcomes in a beautiful, user-friendly interface.
    </p>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-7">
        <a
            href="/players"
            class="block p-6 bg-gray-700 rounded-lg shadow-lg hover:bg-green-500 transition duration-300 text-center"
        >
            <h2 class="text-2xl font-semibold">Players</h2>
            <p class="mt-2 text-gray-200">Explore detailed player statistics and insights.</p>
        </a>
        <a
            href="/teams"
            class="block p-6 bg-gray-700 rounded-lg shadow-lg hover:bg-green-500 transition duration-300 text-center"
        >
            <h2 class="text-2xl font-semibold">Teams</h2>
            <p class="mt-2 text-gray-200">Compare team performance across matches and leagues.</p>
        </a>
        <a
            href="/matches"
            class="block p-6 bg-gray-700 rounded-lg shadow-lg hover:bg-green-500 transition duration-300 text-center"
        >
            <h2 class="text-2xl font-semibold">Matches</h2>
            <p class="mt-2 text-gray-200">Analyze match outcomes and strategies.</p>
        </a>
    </div>
</main>