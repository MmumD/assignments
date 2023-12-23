<template>
    <div class="timeline">
        <div v-for="event in events" :key="event.title" class="timeline-event">
            <div class="event-details">
                <h3>{{ event.title }}</h3>
                <p class="event-date">{{ event.date }}</p>
                <p v-if="event.description" class="event-description">{{ event.description }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    props:{
        events: {
            type: Array,
            required: true
        }
    },
}
</script>

<style>
.timeline {
    border-left: 2px solid #ccc;
    padding-left: 20px;
}

.timeline-event {
    margin-bottom: 20px;
    padding-left: 10px;
}

.event-details {
    background-color: #f9f9f9;
    border-radius: 5px;
    padding: 10px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.event-date {
    font-style: italic;
    margin-bottom: 5px;
}

.event-description {
    font-size: 14px;
    color: #555;
}
</style>