<script>
  import Modal from './event-form.svelte';

  let showModal = $state(false);
  //Change this to interact with data
  let EventTable = [
    {
      Title: "Jogging Day",
      "Start Date": "2025-4-20",
      "Start Time": "9:00AM",
      "End Date": "2025-4-20",
      "End Time": "10:00AM",
    },
    {
      Title: "Running Day",
      "Start Date": "2025-4-25",
      "Start Time": "9:00AM",
      "End Date": "2025-4-20",
      "End Time": "10:00AM",
    },
  ];
</script>

<div class="event_header">
  <h2 class="title_event_header">Event List</h2>
  <button class="event-create-button" onclick={() => (showModal = true)}>Create New Event</button>
  <Modal bind:showModal />
</div>  

<table>
  <thead>
    <tr>
      {#each Object.keys(EventTable[0]) as columnHeading}
        <th>{columnHeading}</th>
      {/each}
      <th>Action</th>
    </tr>
  </thead>
  <tbody>
    {#each Object.values(EventTable) as row}
      <tr>
        {#each Object.values(row) as cell}
          <td>{cell}</td>
        {/each}
        <td>
          <div class="edit-button-group">
            <button class="edit-event-button" aria-label="Edit" onclick={() => (showModal = true)}>
              <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960" width="24px">
                <path d="M200-120q-33 0-56.5-23.5T120-200v-560q0-33 23.5-56.5T200-840h357l-80 80H200v560h560v-278l80-80v358q0 33-23.5 56.5T760-120H200Zm280-360ZM360-360v-170l367-367q12-12 27-18t30-6q16 0 30.5 6t26.5 18l56 57q11 12 17 26.5t6 29.5q0 15-5.5 29.5T897-728L530-360H360Zm481-424-56-56 56 56ZM440-440h56l232-232-28-28-29-28-231 231v57Zm260-260-29-28 29 28 28 28-28-28Z"/>
              </svg></button>
            <button class="edit-event-button" aria-label="Delete">
              <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960" width="24px">
                <path d="M280-120q-33 0-56.5-23.5T200-200v-520h-40v-80h200v-40h240v40h200v80h-40v520q0 33-23.5 56.5T680-120H280Zm400-600H280v520h400v-520ZM360-280h80v-360h-80v360Zm160 0h80v-360h-80v360ZM280-720v520-520Z"/>
              </svg></button>
          </div>
        </td>
      </tr>
    {/each}
  </tbody>
</table>


<style>
  table {
    width: 100%;
    border-collapse: collapse;
  }

  th, td {
    border: 1px solid black;
    padding: 0.5rem;
    text-align: center;
  }

  .edit-button-group {
    display: flex;
    gap: 0.5rem;
    justify-content: center;
  }

  button {
    cursor: pointer;
  }

  button:hover svg {
    fill: #ffffff;
  }

  .event_header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .title_event_header {
    margin-left: 1rem;
  }

  .event-create-button {
    font-weight: 750;
    padding: 0.7rem 2rem;
}

  .edit-event-button {
    padding: 0.3rem;
  }
</style>
