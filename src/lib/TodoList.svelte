<script>
    import Task from "./Task.svelte";
    export let taskList = [{name:'LOL', isDone:false}, {name:'Eat', isDone:false}, {name:'Shower', isDone:false}]
    
    let text = ""

    function addTask(){
        taskList[taskList.length] = {name:text, isDone:false}
        text = ''
        localStorage.setItem('taskList', JSON.stringify(taskList))
    }

    function removeTask(index){
        taskList.splice(index, 1)
        taskList = taskList
        console.log(taskList)
        localStorage.setItem('taskList', JSON.stringify(taskList))
    }

    function updateDone(index, isDone){
        taskList[index].isDone = isDone
        localStorage.setItem('taskList', JSON.stringify(taskList))
    }
</script>


{#each taskList as task, index}
    <Task name={task.name} 
        isDone={task.isDone} 
        on:isDoneUpdate={(e)=>{updateDone(index, e.detail) }}
        on:delMe={()=>{removeTask(index)}} />
{/each}

<form on:submit|preventDefault={addTask}>
    <input type="text" bind:value={text}> 
    <button type="submit">Submit</button>

</form>


<!-- <button on:click={addTask}>Add</button> -->

<style>
    form{
        margin-bottom: 10px;
    }
</style>
<!-- when inp changes var changes. when var changes inp also changes -->
