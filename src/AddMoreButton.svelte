<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  function handleClick() {
    dispatch('openModal');
  }
</script>

<div class="flex justify-end">
  <button class="btn btn-primary mb-10" type="button" on:click={handleClick}
    >ADD MORE
  </button>
</div>
