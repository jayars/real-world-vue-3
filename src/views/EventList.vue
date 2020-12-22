<template>
  <div class="events">
    <h1>Events For Good</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue"
import EventService from "@/services/EventService"

export default {
  name: "EventList",
  data() {
    return {
      events: null,
    }
  },
  async created() {
    try {
      const response = await EventService.getEvents()
      console.log(response)
      this.events = response.data
    } catch (err) {
      console.error(err)
    }
  },
  components: {
    EventCard,
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
