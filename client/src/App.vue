<template lang="html">
  <div>
    <booking-form></booking-form>
    <booking-list :bookingsList="bookings"></booking-list>
  </div>
</template>

<script>
import BookingService from '@/services/BookingService.js';
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
    this.fetchBookings();
    eventBus.$on('add-booking', (booking) => {
      this.bookings.push(booking)
    });

    eventBus.$on('delete-booking', (id) => {
      const index = this.bookings.findIndex(booking => booking._id === id);
      this.bookings.splice(index, 1);
    });
  },
  methods: {
    fetchBookings(){
      BookingService.getBookings().then(bookingItems => this.bookings = bookingItems);
    }
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
