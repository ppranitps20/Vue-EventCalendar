<template>
  <div id="calendar-week" class="container">
    <div class="columns is-multiline">
      <CalendarDay v-for="day in sharedState.seedData" :key="day.id" :day="day"/>
    </div>
  </div>
</template>

<script>
import { store } from '../store';
import CalendarDay from './CalendarDay.vue';

export default {
  name: 'CalendarWeek',
  data() {
    return {
      sharedState: store.state,
    };
  },
  components: {
    CalendarDay,
  },
};
</script>

<style lang="scss" scoped>
.columns {
  display: flex;
  flex-wrap: wrap;
  flex-flow:row;
  justify-content: flex-start;
  margin: 0 auto;
}

#calendar-week {
  margin: 0px 10px 50px 10px;
  .column {
    padding: 0 0 0 0;
    margin: 10px;
    flex-basis: 20em;
    flex-grow: 0;
  }
}
</style>
