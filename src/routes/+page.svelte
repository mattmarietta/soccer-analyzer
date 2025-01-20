
<script>
    let darkMode = false;

    function toggleDarkMode() {
        darkMode = !darkMode;
        document.documentElement.classList.toggle('dark', darkMode);
    }
</script>

<button 
    on:click={toggleDarkMode} 
    class="fixed top-4 right-4 bg-gray-800 text-white p-2 rounded"
>
    Toggle Dark Mode
</button>

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
