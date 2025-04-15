<script>
  import CalendarView from "./components/calendar.svelte";
  import EventList from "./components/event-list.svelte";
</script>

<main class="layout">
  <section class="title">
    <h1>Dashboard</h1>
  </section>
  <section class="calendar">
    <CalendarView />
  </section>
  <br />
  <section class="event_list">
    <EventList />
  </section>
</main>

<style>
  .layout {
    display: grid;
    grid-template-columns: 2fr 1fr;
    grid-template-rows: 1fr 1fr;
    height: 90dvh;
    gap: 1rem;
    padding: 1rem;
    grid-template-areas:
      "title-box event_list-box"
      "calendar-box event_list-box";
  }

  .title {
    grid-area: title-box;
  }

  .calendar {
    grid-area: calendar-box;
    border: 1px solid #ccc;
    border-radius: 1rem;
    padding: 1rem;
  }

  .event_list {
    grid-area: event_list-box;
    border: 1px solid #ccc;
    border-radius: 1rem;
    padding: 1rem;
  }
</style>
