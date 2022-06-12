

<script lang="ts">
  import EmptyState from "./EmptyState.svelte";
  import TaskItem from "./TaskItem.svelte";

  interface ITaskItem {
    id: string;
    title: string;
    isCompleted: boolean;
  }
  
  export let tasks: ITaskItem[];
  export let handleRemoveTask: (taskId: string) => void;
  export let toggleTaskComplete: (taskId: string) => void;
  
  $: createdTasks = tasks.length;
  $: completedTasks = tasks.filter(task => task.isCompleted).length;
</script>

<div class="container">
  <header >
    <p>Created tasks <span>{createdTasks}</span></p>
    <p>Completed <span>{completedTasks} of {createdTasks}</span></p>
  </header>

  {#if tasks.length !== 0}
    <div class="list">
      {#each tasks as task}
        <TaskItem 
          title={task.title}
          id={task.id}
          isCompleted={task.isCompleted}
          handleRemoveTask={handleRemoveTask}
          toggleTaskComplete={toggleTaskComplete}
        />
      {/each}
    </div>
  {:else}
       <EmptyState />
  {/if}
</div>

<style>

  div.container {
    margin-top: 4rem;
  }

  header {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }

  header p {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 8px;

    font-weight: bold;
    color: var(--blue);
  }

  header p span {
    padding: 2px 8px;
    color: var(--gray-200);
    border-radius: 999px;
    background: var(--gray-400);
  }

  div.list {
    display: flex;
    flex-direction: column;
    gap: 12px;

    margin-top: 24px;
  }
</style>
