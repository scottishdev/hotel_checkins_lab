<template lang="html">
  <div>
    <li>
      <p>{{booking.name}}</p>
      <p>{{booking.email}}</p>
      <button v-if="!booking.checkIn" v-on:click="updateBooking">check-in</button>
      <button v-on:click="deleteBooking">delete</button>
    </li>
  </div>
</template>

<script>
import {eventBus} from '@/main.js';
import BookingService from '@/services/BookingService.js';

export default {
  name: 'booking-list-item',
  props: ['booking'],
  methods: {
    deleteBooking(){
      BookingService.deleteBooking(this.booking._id)
      .then(() => eventBus.$emit('delete-booking', this.booking._id));
    },
    updateBooking(){
      const updatedBooking = {
        checkIn: true
      };
      BookingService.updateBooking(updatedBooking, this.booking._id)
      .then(bookingItem => eventBus.$emit('amended-checkin-status', bookingItem));
    }
  }
}
</script>

<style lang="css" scoped>
</style>

function add(){
  return num1 + num2
}
