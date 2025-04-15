<script>
    import Calendar from '@event-calendar/core';
    import DayGrid from '@event-calendar/day-grid';
    import TimeGrid from '@event-calendar/time-grid';

    let plugins = [DayGrid, TimeGrid];
    let options = {
        height: "75dvh",
        headerToolbar: {
            start:'today',
            center: 'title',
            end: 'dayGridMonth,timeGridWeek,timeGridDay prev,next'
        },
        view: 'dayGridMonth',

        //Change this to interact with data (use eventSource)
        events: [{
            title: 'Jogging Day',
            start: '2025-4-20T09:00',
            end: '2025-4-20T10:00'
        },
        {
            title: 'Running Day',
            start: '2025-4-25T09:00',
            end: '2025-4-25T10:00'
        }
    ]
    };
</script>

<Calendar {plugins} {options} />