<script>
  import { createEventDispatcher } from 'svelte';

  export let todos;

  const dispatch = createEventDispatcher();

  function handleCick(event) {
    dispatch('markDone', {
      todo: event.target.previousElementSibling.textContent,
    });
  }
</script>

<section>
  <ul class="space-y-5">
    {#each todos as item}
      <li
        class="px-6 py-4 flex justify-between items-center border border-dashed rounded-lg font-medium text-purple-700 text-left text-xl"
      >
        <span>
          {item}
        </span>
        <button class="btn btn-sm btn-outline btn-primary" on:click={handleCick}>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            class="inline-block w-6 h-6 mr-2 stroke-current"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
          DONE
        </button>
      </li>
    {:else}
      <p class="font-extralight text-xl">
        You're all caught up, please add something!
      </p>
    {/each}
  </ul>
</section>

<style>
</style>
