<script lang="ts">
    import { createEventDispatcher } from "svelte";

    export let title: string;
    export let body: string;
    export let imgUrl: string;
    export let leagueID: number;

    const dispatch = createEventDispatcher<{ select: {id: number} }>();

    //Needs to accept event where it is clicked now
    function handleClick() {
        //Emit a custom event with the league ID
        dispatch("select", {id : leagueID});
    }
  </script>
  
  <div 
    class="flex items-center gap-4 p-4 border rounded-lg shadow-md cursor-pointer transition-transform transform hover:scale-105 hover:bg-gray-100"
    on:click={handleClick}
>
    <img src="{imgUrl}" alt="League Logo" class="w-16 h-16 rounded-md" />
    <div>
        <h2 class="text-lg font-semibold">{title}</h2>
        <p class="text-gray-600 text-sm">{body}</p>
    </div>
</div>