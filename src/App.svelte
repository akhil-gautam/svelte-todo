<script>
  import { onMount } from 'svelte';

  import AddToDo from './AddMoreButton.svelte';
  import Header from './Header.svelte';
  import Modal from './Modal.svelte';
  import ToDoList from './ToDoList.svelte';

  let isModalOpen = false;
  let todos = [];

  onMount(function () {
    todos = getExistingToDos();
  });

  function getExistingToDos() {
    return JSON.parse(localStorage.getItem('svelteToDo')) || [];
  }

  function toggleModal() {
    isModalOpen = !isModalOpen;
  }

  function removeToDo(event) {
    const existingToDos = getExistingToDos();
    const index = existingToDos.indexOf(event.detail.todo);
    if (index > -1) {
      existingToDos.splice(index, 1); // remove that specific todo
      localStorage.setItem('svelteToDo', JSON.stringify(existingToDos)); // save the remaining back
      todos = existingToDos;
    }
  }

  function saveToLocalStorage(event) {
    const existingToDos = getExistingToDos();
    localStorage.setItem(
      'svelteToDo',
      JSON.stringify([...existingToDos, event.detail.todo])
    );

    todos = [...existingToDos, event.detail.todo]; //load newly added todos
    isModalOpen = !isModalOpen; //close the modal form
  }
</script>

<main class="py-4 px-2">
  <Header />
  <AddToDo on:openModal={toggleModal} />
  {#if isModalOpen}
    <Modal on:closeModal={toggleModal} on:saveToDoItem={saveToLocalStorage} />
  {/if}
  <ToDoList {todos} on:markDone={removeToDo} />
</main>
