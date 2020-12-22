<template>
  <router-link :to="url" class="event-link">
    <div class="event-card">
      <!-- Display event data -->
      <span>@ {{ event.time }} on {{ event.date }}</span>
      <h4>{{ event.title }}</h4>
    </div>
  </router-link>
</template>

<script>
export default {
  props: {
    event: {
      type: Object,
      required: true,
    },
  },
  computed: {
    url() {
      return { name: "EventDetails", params: { id: this.event.id } }
    },
  },
}
</script>

<style scoped>
.event-card {
  padding: 20px;
  width: 250px;
  cursor: pointer;
  border: 1px solid #39495c;
  margin-bottom: 18px;
  transition: 0.2s;
}

.event-card:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
  transition: 0.1s;
}

.event-link {
  text-decoration: none;
  color: #2c3e50;
}

</style>
