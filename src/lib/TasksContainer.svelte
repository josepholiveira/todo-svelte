<script lang="ts">
  import CreateTaskForm from "./CreateTaskForm.svelte";
  import TaskList from "./TaskList.svelte";

  import { v4 as uuid} from 'uuid';

  interface ITaskItem {
    id: string;
    title: string;
    isCompleted: boolean;
  }

  let tasks: ITaskItem[] = [
    {
      id: uuid(),
      title: 'Do something',
      isCompleted: false,
    },
    {
      id: uuid(),
      title: 'Do something else',
      isCompleted: false,
    },
  ]


  function addTask(title: string) {
    const newTask = {
      id: uuid(),
      title,
      isCompleted: false,
    };
    
    tasks = [newTask, ...tasks]
  }

  function handleRemoveTask(taskId: string) {
    tasks = tasks.filter(task => task.id !== taskId)
  }

  function toggleTaskComplete(taskId: string) {
    tasks = tasks.map(task => {
      if (task.id === taskId) {
        task.isCompleted = !task.isCompleted
      }
      return task
    })
  }
</script>

<div>
  <CreateTaskForm addTask={addTask}  />
  <TaskList tasks={tasks} handleRemoveTask={handleRemoveTask} toggleTaskComplete={toggleTaskComplete} />
</div>

<style>
  div {
    margin: 0 auto;
    max-width: 736px;
  }
</style>
