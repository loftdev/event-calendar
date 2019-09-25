<template>
      <div id="app">
        <div class="main">
          <div class="calendar-holder">
            <calendar :events="events" />
          </div>
          <div class="form-holder">
            <h3>Schedule an event</h3>
            <event-form />
          </div>
        </div>
      </div>
    </template>
<script>
    import Calendar from './components/Calendar.vue'
    import EventForm from './components/EventForm.vue'
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
            start     : '2019-09-27',
            cssClass  : 'blue',
            YOUR_DATA : {}
          },
          {
            title     : 'event2',
            start     : '2019-09-28',
            end       : '2019-09-30',
            cssClass  : ['orange']
          }] 
        }
      },
      created(){
        const pusher = new Pusher("8f87ec786b8567c2ba25", {
          cluster: "ap3",
          encrypted: true,
        });
        const channel = pusher.subscribe('schedule');
        channel.bind('new-event', (data) => {
          this.events = [
            ...this.events,
            data
          ];
        })
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
