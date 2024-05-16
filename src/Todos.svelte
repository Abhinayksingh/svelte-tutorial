<script>
  let todos = [
    { done: false, text: "Lean svelte" },
    { done: false, text: "Read svelte doc" },
    { done: false, text: "Learn basic of svelte" },
  ];

  const addTodoList = () => {
    todos = [...todos, { done: false, text: "" }];
  };

  const deleteTodos = () => {
    todos = todos.filter((todo) => !todo.done);
  };

  $: remainig = todos.filter((todo) => !todo.done).length;
</script>

<main>
  <h1>Todos</h1>
  <div>
    {#each todos as todo, index (index)}
      <div class="todos">
        <input type="checkbox" bind:checked={todo.done} />
        <input
          type="text"
          placeholder="Please enter todo"
          bind:value={todo.text}
          disabled={todo.done}
        />
      </div>
    {/each}
    <p>{remainig} remaining</p>
    <button on:click={addTodoList}>Add Todo</button>
    <button on:click={deleteTodos}>Delete Todo</button>
  </div>
</main>

<style>
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .todos {
    display: flex;
    gap: 5px;
  }
</style>
