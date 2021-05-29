<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  function handleClick() {
    dispatch('openModal');
  }

</script>

<div class="flex justify-center mt-10 mb-4">
  <button class="btn btn-block btn-sm btn-primary" type="button" on:click={handleClick}
    >ADD MORE
  </button>
</div>
