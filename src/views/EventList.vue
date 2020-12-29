<template>
  <div class="events">
    <h1>Events For Good</h1>
    <event-card
        v-for="event in events"
        :key="event.id"
        :event="event"
    />
  </div>
</template>

<script>
import EventCard from "@/components/EventCard";
import EventServices from "@/services/EventService";
export default {
  name: 'EventList',
  components: {
    EventCard
  },
  data() {
    return {
      events: null
    }
  },
  created() {
    EventServices.getEvents().then(response => {
      this.events = response.data;
    }).catch(error => {
      console.log(error)
    })
  },
}
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}

</style>
