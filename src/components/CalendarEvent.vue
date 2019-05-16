<template>
  <div class="day-event" :style="getEventBackgroundColor">
    <div v-if="!event.edit">
      <span class="has-text-centered details">{{ event.details }}</span>
      <div class="has-text-centered icons">
        <i class="fa fa-pencil-square edit-icon"
        @click="editEvent(day.id, event.details)"></i>
        <i class="fa fa-trash-o delete-icon" @click="deleteEvent(day.id, event.details)"></i>
      </div>
    </div>
    <div v-if="event.edit">
      <input type="text" :placeholder="event.details" v-model="newEventDetails"/>
      <div class="has-text-centered icons">
        <i class="fa fa-check" @click="updateEvent(day.id, event.details, newEventDetails)"></i>
      </div>
    </div>
  </div>
</template>

<script>
import { store } from '../store';

export default {
  name: 'CalendarEvent',
  props: ['event', 'day'],
  data() {
    return {
      newEventDetails: '',
    };
  },
  methods: {
    editEvent(dayId, eventDetails) {
      store.editEvent(dayId, eventDetails);
    },
    updateEvent(dayId, originalEventDetails, updatedEventDetails) {
      if (updatedEventDetails === '') {
        store.updateEvent(dayId, originalEventDetails, originalEventDetails);
      } else {
        store.updateEvent(dayId, originalEventDetails, updatedEventDetails);
        this.newEventDetails = '';
      }
    },
    deleteEvent(dayId, eventDetails) {
      store.deleteEvent(dayId, eventDetails);
    },
  },
  computed: {
    getEventBackgroundColor() {
      const colors = ['#f53b57', '#3c40c6', '#05c46b', '#ffa801'];
      const randomColor = colors[Math.floor(Math.random() * colors.length)];
      return `background-color: ${randomColor}`;
    },
  },
};
</script>

<style lang="scss" scoped>
.day-event {
  margin-top: 6px;
  margin-bottom: 6px;
  display: block;
  color: #fff;
  padding: 5px;
  border-radius: 10px;

  .details {
    font-size: 14px;
    display: block;
  }

  .icons .fa {
    padding: 5px 5px;
    font-size: 2em;
  }

  input {
    background: none;
    border: 0;
    border-bottom: 1px solid #fff;
    width: 100%;

    &:focus {
      outline: none;
    }
  }
}
</style>
