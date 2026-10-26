<script>
export default {
  props: ['room'],

  methods: {
    viewRoom() {
      this.$emit('viewRoom', this.room)
    },
    bookRoom(){
      this.$emit('bookRoom', this.room)
    }
  }
}
</script>

<template>
  <div class="bg-white p-3 rounded shadow">

    <img :src="room.image"
      class="w-full h-40 object-cover rounded">

    <h2 class="font-bold mt-3">
      {{ room.name }}
    </h2>

    <p>Guests: {{ room.capacity }}</p>

    <p class="font-bold">
      ${{ room.price }} per night
    </p>

    <div class="flex gap-2 mt-3">

  <button @click="viewRoom"
    class="bg-[#302218] text-white p-2 rounded">
    View Details
  </button>

  <button @click="bookRoom"
    class="bg-green-700 text-white p-2 rounded">
    Book Now
  </button>

</div>
  </div>
</template>