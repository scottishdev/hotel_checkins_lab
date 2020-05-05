<template lang="html">
<booking-form></booking-form>
</template>

<script>

import BookingForm from '@/components/BookingForm.vue';
import BookingList from '@/components/BookingList.vue';
import {eventBus} from '@/main.js';

export default {
  name: 'App',
  data(){
    return {
      bookings: []
    }
  },
  components: {
    'booking-form': BookingForm,
    'booking-list': BookingList
  },
  mounted(){
    

    eventBus.$on('add-booking', (booking) => {
      this.bookings.push(booking)
    });
  }

}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
