<script>
  import Tasks from "./Tasks.svelte";

  let tasks = [];
  let newTask = "";

  const addTask = () => {
    if (newTask.trim() !== "") {
      // Se añade la nueva tarea al array de tareas
      tasks = [...tasks, { text: newTask, completed: false }];
      newTask = ""; // Se limpia el campo de entrada
    }
  };

  // Funciones para modificar las tareas existentes
  const toggleComplete = (index) => {
    tasks = tasks.map((task, i) =>
      i === index ? { ...task, completed: !task.completed } : task
    );
  };

  // Función para eliminar una tarea del array
  const deleteTask = (index) => {
    tasks = tasks.filter((_, i) => i !== index);
  };
</script>

<div class="row mt-5">
  <div class="col-md-5">
    <h2 class="text-center mb-4 fw-bold">Registrar Nueva Tareas</h2>

    <div class="input-group mb-3">
      <input
        type="text"
        class="form-control"
        placeholder="Escribe una nueva tarea..."
        bind:value={newTask}
      />
    </div>
   <button class="btn btn-primary w-100" on:click={addTask}>Agregar</button>
  </div>

  <div class="col-md-7">
    <!-- Se pasan las funciones toggleComplete y deleteTask como props -->
    <Tasks {tasks} {toggleComplete} {deleteTask} />
  </div>
</div>
