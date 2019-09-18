<template>
  <div id="app">
    <div class="main">
      <div class="calendar-holder">
        <Calendar :events="events" />
      </div>
      <div class="form-holder">
        <h3>Schedule an event</h3>
        <EventForm />
      </div>
    </div>
  </div>
</template>

<script>
import Calendar from './components/Calendar.vue'
import EventForm from './components/EventForm'
import Pusher from 'pusher-js';
export default {
  name: 'app',
  components: {
    Calendar,
    EventForm
  },
  data(){
    return {
      events: [{
        title     :  'event1',
        start     : '2018-07-09',
        cssClass  : 'blue',
        YOUR_DATA : {}
      },
      {
        title     : 'event2',
        start     : '2018-07-10',
        end       : '2018-07-13',
        cssClass  : ['orange']
      }] 
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.main {
  display: flex;
  align-items: center;
}
.calendar-holder {
  width: 65%;
}
.form-holder {
  width: 35%;
}
.form-holder > h3 {
  color: orangered;
  text-transform: uppercase;
  font-size: 16px;
  text-align: left;
  margin-left: 30px;
  margin-bottom: 10px;
}
</style>
