<template>
  <div class="day column " @click="setActiveDay(day.id)">
      <div class="day-banner has-text-centered">{{ day.abbvTitle }}</div>
      <div class="day-details">
        <div class="day-number">{{ day.id }}</div>
        <CalendarEvent v-for="(event, index) in day.events"
          :key="index"
          :event="event"
          :day="day"/>
      </div>
  </div>
</template>

<script>
import CalendarEvent from './CalendarEvent.vue';
import { store } from '../store';

export default {
  name: 'CalendarDay',
  props: ['day'],
  methods: {
    setActiveDay(dayId) {
      store.setActiveDay(dayId);
    },
  },
  components: {
    CalendarEvent,
  },
};
</script>

<style lang="scss" scoped>
.day {
  border-radius: 10px;
  background-color: #34495e;
  color: #fff;
  font-size: 12px;
  cursor: pointer;

  &:hover {
    background: darken(#4a4a4a, 3%);
  }

  .day-banner {
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    background-color: #34495e;
    color: #fff;
    padding: 10px;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-size: 12px;
    font-weight: 600;
  }

  .day-details {
    padding: 10px;
  }
}
</style>
