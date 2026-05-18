<script>
  let tasks = [];
  let input = "";

  function addTask() {
    if (!input.trim()) return;
    tasks = [...tasks, { text: input, done: false }];
    input = "";
  }

  function deleteTask(index) {
    tasks = tasks.filter((_, i) => i !== index);
  }
</script>

<div class="todo-container">
  <h2>Att göra-lista</h2>

  <div class="input-group">
    <input
      bind:value={input}
      placeholder="Skriv en uppgift..."
      on:keydown={(e) => e.key === 'Enter' && addTask()}
    />
    <button on:click={addTask}>Lägg till</button>
  </div>
  <ul>
    {#each tasks as task, index}
      <li>
        <span class="task-text">{task.text}</span>
        <button class="delete-btn" on:click={() => deleteTask(index)}>
          ×
        </button>
      </li>
    {/each}
  </ul>
</div>
