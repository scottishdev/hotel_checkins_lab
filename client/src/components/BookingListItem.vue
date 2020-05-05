<template lang="html">
  <div>
    <li>
      <p>{{booking.name}}</p>
      <p>{{booking.email}}</p>
      <button v-on:click="updateBooking">check-in</button>
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
      
    }
  }
}
</script>

<style lang="css" scoped>
</style>

function add(){
  return num1 + num2
}
