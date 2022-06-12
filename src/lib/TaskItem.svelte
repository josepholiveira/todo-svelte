<script lang="ts">
  import TrashIcon from "phosphor-svelte/lib/Trash";

  export let title: string;
  export let id: string;
  export let isCompleted: boolean;
  export let handleRemoveTask: (taskId: string) => void;
  export let toggleTaskComplete: (taskId: string) => void;
</script>

<div class={`task-item ${isCompleted && 'completed'}`}>
  <div class="checkbox-round">
    <input type="checkbox" bind:checked={isCompleted} id={`checkbox-${id}`} on:change={() => toggleTaskComplete(id)} />
    <label for={`checkbox-${id}`}></label>
  </div>

  {title}

  <button on:click={() => handleRemoveTask(id)}>
    <TrashIcon color="#808080" size="20" />
  </button>
</div>

<style>
  .task-item {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    padding: 16px;
    gap: 12px;

    background: var(--gray-500);
    border: 1px solid var(--gray-400);
    box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.06);
    border-radius: 8px;
  }

  .completed {
    text-decoration-line: line-through;
    color: var(--gray-300);
  }

  button {
    background: transparent;
    border: none;
    cursor: pointer;
    margin-left: auto;
  }

  .checkbox-round {
    position: relative;
    height: 20px;
    width: 20px;
  }

  .checkbox-round label {
    background-color: transparent;
    border: 2px solid var(--blue);
    border-radius: 50%;
    cursor: pointer;
    height: 20px;
    left: 0;
    position: absolute;
    top: 0;
    width: 20px;
  }

  .checkbox-round label:after {
    border: 2px solid #fff;
    border-top: none;
    border-right: none;
    content: "";
    height: 4px;
    left: 3px;
    opacity: 0;
    position: absolute;
    top: 4px;
    transform: rotate(-45deg);
    width: 8px;
  }

  .checkbox-round input[type="checkbox"] {
    visibility: hidden;
  }

  .checkbox-round input[type="checkbox"]:checked + label {
    background-color: var(--purple-dark);
    border-color: var(--purple-dark);
  }

  .checkbox-round input[type="checkbox"]:checked + label:after {
    opacity: 1;
  }
</style>