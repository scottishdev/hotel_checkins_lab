<template lang="html">
  <div>
    <booking-list-item v-for="(booking, index) in bookingsList" :key="index" :booking="booking"></booking-list-item>
  </div>
</template>

<script>
import BookingListItem from '@/components/BookingListItem.vue'

export default {
  name: 'booking-list',
  props: ['bookingsList'],
  components: {
    'booking-list-item': BookingListItem
  }
}
</script>

<style lang="css" scoped>
</style>
