<script>
  let { showModal = $bindable() } = $props();
  let dialog = $state();

  $effect(() => {
    if (showModal) dialog.showModal();
  });
</script>

<dialog
  class="event-form"
  bind:this={dialog}
  onclose={() => (showModal = false)}
  onclick={(e) => {
    if (e.target === dialog) dialog.close();
  }}
>
  <section>
    <h2>Create New Event</h2>
  </section>
  <section class="form-details">
    <label class="label-1">Event Name: <input type="text" /></label>
    <label class="label-2">Start Date: <input type="date" /></label>
    <label class="label-3">Start Time: <input type="time" /></label>
    <label class="label-4">End Date: <input type="date" /></label>
    <label class="label-5">End Time: <input type="time" /></label>
  </section>
  <section class="form-button">
    <!-- svelte-ignore a11y_autofocus -->
    <button autofocus onclick={() => dialog.close()}>Save</button>
    <button onclick={() => dialog.close()}>Cancel</button>
  </section>
</dialog>

<style>
  .label-1 {grid-area: label-1}
  .label-2 {grid-area: label-2}
  .label-3 {grid-area: label-3}
  .label-4 {grid-area: label-4}
  .label-5 {grid-area: label-5}

  .form-details {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr;
    grid-template-areas:
    "label-1 label-1"
    "label-2 label-3"
    "label-4 label-5";
  }

  .form-details > label {
    padding: 0.5rem 0.5rem;
  }

  .form-details > label > input {
    box-sizing: border-box;
    width: 100%;
  }

  .form-button {
    display: flex;
    justify-content: flex-end;
    gap: 1rem;
    padding: 0 0.5rem;
    margin-top: 1rem;
  }

  .form-button > button {
    width: 5rem;
  }

  h2 {
    text-align: center;
  }
</style>
