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

<button onclick={() => (showModal = true)}>Create New Event</button>

<Modal bind:showModal />

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
        <td><button>Edit Row</button></td>
      </tr>
    {/each}
  </tbody>
</table>


<style>
  table {
    width: 100%;
    border-collapse: collapse;
  }

  th,
  td {
    border: 1px solid #ddd;
    padding: 0.5rem;
    text-align: center;
  }
</style>
