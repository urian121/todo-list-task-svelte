<script>
  // Declarar las props que el componente espera recibir
  export let tasks = [];
  export let toggleComplete;
  export let deleteTask;
</script>

{#if tasks.length > 0}
    
  <ul class="list-group">
    {#each tasks as task, index}
      <li class="list-group-item d-flex justify-content-between align-items-center py-2">
          <input
            type="checkbox"
            class="form-check-input me-2"
            checked={task.completed}
            on:change={() => toggleComplete(index)}
          />
          <span class:completed={task.completed}>{task.text}</span>
        <button class="btn btn-danger btn-sm" type="button" aria-label="Delete" on:click={() => deleteTask(index)}>
          <i class="bi bi-trash3"></i>
        </button>
      </li>
    {/each}
  </ul>
{:else}
  <p class="text-center text-muted">No hay tareas pendientes 😒.</p>
{/if}

<style>
  .completed {
    text-decoration: line-through;
    color: gray;
  }
  .form-check-input {
    width: 25px;
    height: 25px;
  }	
</style>
