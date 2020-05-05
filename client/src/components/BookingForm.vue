<template lang="html">
  <form method="post" v-on:submit.prevent="addBooking">
    <label for="name">Guest Name:</label>
    <input type="text" v-model="name" required>

    <label for="email">Guest Email:</label>
    <input type="text" v-model="email" required>

    <input type="submit" value="submit Booking">
  </form>
</template>

<script>
import {eventBus} from '@/main.js';
import BookingService from '@/services/BookingService.js';

export default {
  name: 'booking-form',
  data(){
    return {
      name: '',
      email: ''
    }
  },
  methods: {
    addBooking() {
      const newBooking = {
        name: this.name,
        email: this.email,
        checkIn: false
      };
      BookingService.postBooking(newBooking)
      .then(bookingItem => eventBus.$emit('add-booking', bookingItem));
    }
  }
}
</script>

<style lang="css" scoped>
</style>
