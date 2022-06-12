<script lang="ts">
  import PlusCircleIcon from "phosphor-svelte/lib/PlusCircle";

  export let addTask: (title: string) => void;

  let newTaskTitle = '';

  function handleAddTask() {
    addTask(newTaskTitle)

    newTaskTitle = ''
  }
</script>

<div>
  <input placeholder="Add a new task" bind:value={newTaskTitle} />
  <button on:click={handleAddTask} disabled={newTaskTitle.length === 0}>
    Add
    <PlusCircleIcon color="#F2F2F2" size={16} weight="bold" />
  </button>
</div>
  
<style>
  div {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 8px;

    margin-top: -27px;
  }

  input {
    height: 54px;
    background: var(--gray-500);

    border: 1px solid var(--gray-700);
    border-radius: 8px;
  
    flex: 1;

    padding: 16px;
    color: var(--gray-300);
  }

  button {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 8px;
    font-size: 0.875rem;

    padding: 16px;
    background: var(--blue-dark);
    border: 0;
    border-radius: 8px;
    font-weight: bold;
    color: var(--gray-100);

    transition: filter 0.15s;
    cursor: pointer;
  }

  button:disabled {
    filter: brightness(0.7);
    cursor: not-allowed; 
  }

  button:not(:disabled):hover {
    filter: brightness(0.8)
  }
</style>