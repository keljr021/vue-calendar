<template>
    <div>
        <div class="event-header">Upcoming Events: </div>
        <div class="event-box">
            <div class="event-item">
                <span class="event-time">10:00 AM</span>
                <span class="event-desc">Event</span>
            </div>
            <div class="event-item">
                <span class="event-time">10:00 AM</span>
                <span class="event-desc">Event</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CalEvents'
    
}
</script>

<style scoped>

    .event-header {
        padding: 10px 5px;
        font-size: 18px;
        text-align: left;
    }

    .event-box {
        background: #bbb;
        text-align: left;
    }

    .event-item {
        padding: 10px;
    }

    .event-time, .event-desc {
        padding: 10px 5px;
    }
</style>