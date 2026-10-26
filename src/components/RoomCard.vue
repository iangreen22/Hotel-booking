<script>
export default {
  props: ['room'],

  methods: {
    viewRoom() {
      this.$emit('viewRoom', this.room)
    },
    bookRoom() {
      this.$emit('bookRoom', this.room)
    }
  }
}
</script>

<template>
  <div class="bg-white px-20 py-30 rounded shadow grid grid-cols-3 min-h-screen gap-20 ">
    <div v-for="unit in room" :key="unit.id" class="px-5">
      <div class="w-full">
        <img :src="unit.image" class="w-full h-40 object-cover rounded">

        <h2 class="font-bold mt-3">
          {{ unit.name }}
        </h2>

        <p>Guests: {{ unit.capacity }}</p>

        <p class="font-bold">
          ${{ unit.price }} per night
        </p>

        <div class="flex gap-2 mt-3">

          <button @click="viewRoom" class="bg-[#302218] text-white p-2 rounded cursor-pointer hover:bg-[#302218]/80">
            View Details
          </button>

          <button @click="bookRoom" class="bg-green-700 text-white p-2 rounded cursor-pointer hover:bg-green-600">
            Book Now
          </button>
        </div>
      </div>
    </div>
  </div>
</template>