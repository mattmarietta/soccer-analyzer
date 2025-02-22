<script lang="ts">
    import { onMount } from "svelte";
    import { page } from "$app/state"; 
    import { writable } from "svelte/store";
    import { goto } from "$app/navigation";
    import {get} from 'svelte/store';
    import ListItem from "../../components/ListItem.svelte"; 


    let countries = writable([]);

    // Fetch countries from the API
    onMount(async () => {

        const response = await fetch(`https://v3.football.api-sports.io/countries`, {
            method: 'GET',
            headers: { 'x-rapidapi-key': '''' }
        });

        const data = await response.json();
        countries.set(data.response || []);
    });

    function handleCountrySelect(event){
        const countryName = event.detail.id;
        goto(`/leagues/${countryName}`);
    }
</script>

<h1>Select a Country</h1>
<div class="overflow-y-auto grid grid-cols-3 gap-2">
    {#each $countries as country}
        <ListItem
            itemID={country.name}
            title={country.name}
            imgUrl={country.flag}
            on:select={handleCountrySelect}
        />
    {/each}
</div>
