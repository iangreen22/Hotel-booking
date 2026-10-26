<script>
export default {
  props: ['room'],

  methods: {
    closeRoom() {
      this.$emit('close')
    }
  }
}
</script>

<template>
  <div class="fixed inset-0 bg-black/50 flex items-center justify-center">

    <div class="bg-white p-6 rounded w-96">

      <h2 class="text-2xl font-bold mb-3">
        {{ unit.name }}
      </h2>

      <img :src="room.image"
        class="w-full h-40 object-cover mb-3">

      <p>Room Type: {{ unit.type }}</p>
      <p>Guests: {{ unit.capacity }}</p>
      <p>Price: ${{ unit.price }} per night</p>

      <h3 class="font-bold mt-3">Amenities</h3>

      <p v-for="item in room.amenities" :key="item">
        • {{ item }}
      </p>

      <button @click="closeRoom"
        class="bg-[#302218] text-white p-2 rounded mt-4">
        Close
      </button>

    </div>
  </div>
</template>