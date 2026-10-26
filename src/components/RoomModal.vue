<script>
export default {
  props: ['modal'],

  methods: {
    closeRoom() {
      this.$emit('close')
    }
  }
}
</script>

<template>
  <div class="fixed inset-0 bg-black/50 flex items-center justify-center">

    <div v-for="i in modal" class="bg-white p-6 rounded w-96">

      <h2 class="text-2xl font-bold mb-3">
        {{ i.name }}
      </h2>

      <img :src="i.image"
        class="w-full h-40 object-cover mb-3">

      <p>Room Type: {{ i.type }}</p>
      <p>Guests: {{ i.capacity }}</p>
      <p>Price: ${{ i.price }} per night</p>

      <h3 class="font-bold mt-3">{{i.amenities}}</h3>


      <button @click="closeRoom"
        class="bg-[#302218] text-white p-2 rounded mt-4 cursor-pointer">
        Close
      </button>

    </div>
  </div>
</template>