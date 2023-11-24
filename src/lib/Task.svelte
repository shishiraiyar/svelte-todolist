<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher()

    export let name;
    export let isDone;

    function handleClick(){
        isDone = !isDone
        dispatch('isDoneUpdate', isDone)
    }
</script>

<div>
    <button class:checked={isDone}
            class:unchecked={!isDone}
            on:click={handleClick}>
        {name}
    </button>
    <button on:click={()=>{dispatch('delMe')}} class="xbutton">❌</button>
</div>

<style>
    .checked, .unchecked{
        min-width: 100px;
        padding: 5px;
    }
    .checked{
        background-color: #008170;
        text-decoration: line-through;
    }
    .unchecked{
        background-color: antiquewhite;
    }
    
    .xbutton{
        min-width: none;
        background-color: darkgray;
        border-radius: 5000px;
        font-size:x-small;
        /* padding: 5px; */
    }
    div{
        margin-top: 10px;
        margin-bottom: 10px;
    }
</style>