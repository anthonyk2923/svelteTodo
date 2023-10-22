<script>
  let todos = [];
  let todoEntered;

  function handleInputSubmit() {
    if (!todoEntered) {
      alert('Please enter a Todo first');
    } else {
      todos = [...todos, todoEntered];
      todoEntered = null;
    }
  }
  function handleDelBtn(item) {
    const index = todos.indexOf(item);
    if (index > -1) {
      // only splice array when item is found
      todos.splice(index, 1); // 2nd parameter means remove one item only
    }
    todos = todos;
  }
</script>

<h1 align="center" class="text-5xl m-3 text-violet-500">Todo List</h1>
<hr class="hr border-yellow-500" />

<div align="center">
  <input
    bind:value={todoEntered}
    type="text"
    class="my-4 text-violet-500 rounded-sm p-1 px-5 shadow-sm shadow-violet-500"
  />
  <button
    on:click={handleInputSubmit}
    class="button bg-violet-500 rounded-sm p-1 px-3 shadow-sm shadow-violet-500"
    >Go!</button
  >
</div>

{#if todos.length !== 0}
  <div align="center" class=" text-4xl mt-12 text-yellow-500">Items</div>
  <div
    class="divide-y relative divide-yellow-500 m-24 mt-2 border border-violet-500 p-3"
  >
    {#each todos as todo}
      <div align="center" class="p-2 text-2xl text-violet-500">
        <input
          type="checkbox"
          class="absolute ml-12 left-0 h-8 w-8 rounded-full shadow"
        />
        {todo}

        <div class="absolute right-0 mr-12 top-5 h-8 w-8">
          <button
            on:click={handleDelBtn(todo)}
            class="button bg-violet-500 rounded-sm p-1 shadow-sm shadow-violet-500 text-black"
            ><img
              width="20"
              src="https://cdn-icons-png.flaticon.com/512/542/542724.png"
              alt=""
            /></button
          >
        </div>
      </div>
    {/each}
  </div>
{:else}
  <hr class="hr border-yellow-500 mt-14" />
  <div align="center" class=" text-4xl m-4 text-yellow-500">No Items</div>
  <hr class="hr border-yellow-500" />
{/if}
