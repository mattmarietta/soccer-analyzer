<script>
    // Add any page-specific logic here if needed
</script>

<main class="flex flex-col items-center justify-center text-white">
    <h1 class="text-4xl font-bold mb-4 text-center">
        Welcome to <span class="text-green-400">Soccer Analyzer</span>
    </h1>
    <p class="text-lg mb-8 text-gra
    y-300 text-center max-w-prose">
        Analyze your favorite player, team performance, and match outcomes in a beautiful, user-friendly interface.
    </p>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-7">
        <a
            href="/countries"
            class="block p-6 bg-gray-700 rounded-lg shadow-lg hover:bg-green-500 transition duration-300 text-center"
        >
            <h2 class="text-2xl font-semibold">Search</h2>
            <p class="mt-2 text-gray-200">Explore by looking at countries, leagues, teams, and players.</p>
        </a>
        <a
            href="/teams"
            class="block p-6 bg-gray-700 rounded-lg shadow-lg hover:bg-green-500 transition duration-300 text-center"
        >
            <h2 class="text-2xl font-semibold">Trivia</h2>
            <p class="mt-2 text-gray-200">Try your luck and see if you can guess the correct player given statistics TBI.</p>
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