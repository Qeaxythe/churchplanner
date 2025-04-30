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
  * {
    font-family: system-ui;
    font-weight: 600;
  }

  h1 {
    font-size: xx-large;
    font-weight: 700;
  }
  
  .layout {
    display: grid;
    grid-template-columns: 2fr 1fr;
    grid-template-rows: auto 80dvh;
    gap: 1rem;
    padding: 1rem;
    grid-template-areas:
      "title-box event_list-box"
      "calendar-box event_list-box"
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

  @media(max-width: 1100px){
    .layout{
      grid-template-columns: 1fr;
      grid-template-rows: auto 60dvh auto;
      grid-template-areas:
        "title-box"
        "calendar-box"
        "event_list-box";
    }
  }
</style>
