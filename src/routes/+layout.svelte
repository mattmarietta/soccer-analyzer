<script lang="ts">
    import '../app.css';
    let { children } = $props();
</script>

<nav class="bg-gray-800 p-4 shadow-md">
    <div class="container mx-auto flex items-center justify-between">
        <!-- Logo -->
        <a href="/" class="text-2xl font-bold text-white">
            Soccer Analyzer
        </a>

        <!-- Navigation Links -->
        <ul class="flex space-x-6">
            <li>
                <a
                    href="/"
                    class="text-gray-300 hover:text-white transition font-medium"
                >
                    Home
                </a>
            </li>
            <li>
                <a
                    href="/players"
                    class="text-gray-300 hover:text-white transition font-medium"
                >
                    Players
                </a>
            </li>
            <li>
                <a
                    href="/teams"
                    class="text-gray-300 hover:text-white transition font-medium"
                >
                    Teams
                </a>
            </li>
            <li>
                <a
                    href="/matches"
                    class="text-gray-300 hover:text-white transition font-medium"
                >
                    Matches
                </a>
            </li>
            <li>
                <a
                    href="/about"
                    class="text-gray-300 hover:text-white transition font-medium"
                >
                    About
                </a>
            </li>
        </ul>
    </div>
</nav>

<main class="flex flex-col items-center justify-center min-h-screen bg-gradient-to-br from-gray-800 via-gray-900 to-black text-white">
    {@render children()}
</main>

<style>
    :global(.dark) {
        --bg-color: #1a202c;
        --text-color: #a0aec0;
    }

    :global(body) {
        background-color: var(--bg-color, white);
        color: var(--text-color, black);
    }

    nav {
        background-color: var(--bg-color, #2d3748);
    }

    a {
        color: var(--text-color, white);
    }

    .bg-gradient {
        background: linear-gradient(to right, #2d3748, #4a5568);
    }
</style>