<template>
  <div id="calendar-entry">
    <div class="calendar-entry-note">
      <input type="text" placeholder="New Event" v-model="inputEntry" required/>
      <p class="calendar-entry-day">
        Day of event: <span class="bold">{{ titleOfActiveDay }}</span>
      </p>
      <a class="button is-small is-outlined" @click="submitEvent(inputEntry)">Submit</a>
    </div>
    <p style="color: red; font-size: 13px" v-if="error">
      You must type something.
    </p>
  </div>
</template>

<script>
import { store } from '../store';

export default {
  name: 'CalendarEntry',
  computed: {
    titleOfActiveDay() {
      return store.getActiveDay().fullTitle;
    },
  },
  data() {
    return {
      inputEntry: '',
      error: false,
    };
  },
  methods: {
    submitEvent(eventDetails) {
      if (eventDetails === '') {
        this.error = true;
        return this.error;
      }
      store.submitEvent(eventDetails);
      this.inputEntry = '';
      this.error = false;
      return this.error;
    },
  },
};
</script>

<style lang="scss" scoped>
.button {
  border: 1px solid #ff6b6b;
  color: #ff6b6b;
}

#calendar-entry {
  background: #FFF;
  border: 1px solid #ff6b6b;
  border-radius: 10px;
  max-width: 300px;
  margin: 0 auto;
  padding: 20px;
  margin-bottom: 139px;

  .calendar-entry-note {
    input {
      width: 200px;
      font-weight: 600;
      border: 0;
      border-bottom: 1px solid #CCC;
      font-size: 15px;
      height: 30px;
      margin-bottom: 10px;

      &:focus {
        outline: none;
      }
    }

    .calendar-entry-day {
      color: #ff6b6b;
      font-size: 12px;
      margin-bottom: 10px;
      padding-bottom: 5px;

      .bold {
        font-weight: 600;
      }
    }

    .submit {
      display: block;
      margin: 0 auto;
    }
  }
}
</style>
