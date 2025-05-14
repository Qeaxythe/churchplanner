<script>
  let {
    showModal = $bindable(),
    onSave = () => {},
    editingIndex = null,
    EventTable = [],
  } = $props();
  let dialog = $state();

  let newEvent = $state({
    Title: "",
    "Start Date": "",
    "Start Time": "",
    "End Date": "",
    "End Time": "",
  });

  // Pre-fill the form when editing an event
  $effect(() => {
    if (showModal) {
      dialog.showModal();
      if (editingIndex !== null) {
        // Load the event data into the form for editing
        newEvent = { ...EventTable[editingIndex] };
      } else {
        // Reset the form for creating a new event
        newEvent = {
          Title: "",
          "Start Date": "",
          "Start Time": "",
          "End Date": "",
          "End Time": "",
        };
      }
    }
  });

  function saveEvent() {
    onSave(newEvent);
    dialog.close();
  }
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
    <h2>{editingIndex !== null ? "Edit Event" : "Create New Event"}</h2>
  </section>
  <section class="form-details">
    <label class="label-1"
      >Event Name: <input type="text" bind:value={newEvent.Title} /></label
    >
    <label class="label-2"
      >Start Date: <input
        type="date"
        bind:value={newEvent["Start Date"]}
      /></label
    >
    <label class="label-3"
      >Start Time: <input
        type="time"
        bind:value={newEvent["Start Time"]}
      /></label
    >
    <label class="label-4"
      >End Date: <input type="date" bind:value={newEvent["End Date"]} /></label
    >
    <label class="label-5"
      >End Time: <input type="time" bind:value={newEvent["End Time"]} /></label
    >
  </section>
  <section class="form-button">
    <!-- svelte-ignore a11y_autofocus -->
    <button autofocus onclick={saveEvent}
      >{editingIndex !== null ? "Update" : "Save"}</button
    >
    <button onclick={() => dialog.close()}>Cancel</button>
  </section>
</dialog>

<style>
  dialog {
    border: 0.15rem outset grey;
    border-radius: 1rem;
  }

  .label-1 {
    grid-area: label-1;
  }
  .label-2 {
    grid-area: label-2;
  }
  .label-3 {
    grid-area: label-3;
  }
  .label-4 {
    grid-area: label-4;
  }
  .label-5 {
    grid-area: label-5;
  }

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
