<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();
  let todo = '';

  function handleClick() {
    dispatch('closeModal');
  }

  function handleSubmit() {
    dispatch('saveToDoItem', { todo });
  }
</script>

<div class="absolute top-0 left-0 h-full w-full bg-white bg-opacity-80" />
<div class="absolute left-0 right-0 flex justify-center">
  <div class="modal-box">
    <form on:submit|preventDefault={handleSubmit}>
      <div class="form-control">
        <label for="task" class="label">
          <span class="label-text">#TODO</span>
        </label>
        <input
          id="task"
          type="text"
          placeholder="What do you want to do?"
          class="input input-primary input-bordered"
          bind:value={todo}
        />
      </div>
      <div class="modal-action text-white">
        <button class="btn btn-secondary" on:click={handleClick}>Close</button>
        <button class="btn btn-primary" type="submit">Save</button>
      </div>
    </form>
  </div>
</div>
