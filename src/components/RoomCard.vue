<script>
export default {
  props: ['room'],
  emits: ['toRoom', 'bookRoom'],

  methods: {
    viewRoom(name, type, capacity, image, price, amenities) {
      this.$emit('toRoom', {
        name,
        type,
        capacity,
        image,
        price,
        amenities,
      })
    },

    bookRoom(unit) {
      this.$emit('bookRoom', unit)
    }
  }
}
</script>

<template>
  <section class="w-full min-h-screen bg-white px-4 py-8 sm:px-6 sm:py-10 md:px-8 lg:px-12 xl:px-16">

    <div class="grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-3 xl:gap-8">

      <div v-for="unit in room" :key="unit.id"
        class="flex flex-col overflow-hidden rounded-xl bg-white shadow-md transition duration-300 hover:-translate-y-1 hover:shadow-xl">


        <div class="w-full overflow-hidden">
          <img :src="unit.image" :alt="unit.name"
            class="h-48 w-full object-cover transition duration-300 hover:scale-105 sm:h-52 lg:h-56" />
        </div>


        <div class="flex flex-1 flex-col p-4 sm:p-5">

          <h2 class="text-lg font-bold text-[#302218] sm:text-xl">
            {{ unit.name }}
          </h2>

          <p class="mt-2 text-sm text-gray-600">
            Guests: {{ unit.capacity }}
          </p>

          <p class="mt-2 text-lg font-bold text-[#302218]">
            ₱{{ unit.price }}
            <span class="text-sm font-normal text-gray-500">
              / night
            </span>
          </p>


          <div class="mt-3">
            <p class="text-sm font-semibold text-gray-700">
              Amenities
            </p>

            <div class="mt-2 flex flex-wrap gap-2">
              {{ unit.amenities }}
            </div>
          </div>


          <div class="mt-auto flex flex-col gap-3 pt-5 sm:flex-row">

            <button @click="viewRoom(
              unit.name,
              unit.type,
              unit.capacity,
              unit.image,
              unit.price,
              unit.amenities
            )"
              class="w-full rounded-lg bg-[#302218] px-4 py-3 text-sm font-semibold text-white transition hover:bg-[#302218]/80 focus:outline-none focus:ring-2 focus:ring-[#302218] focus:ring-offset-2 cursor-pointer">
              View Details
            </button>

            <button @click="bookRoom(unit)"
              class="w-full rounded-lg bg-green-700 px-4 py-3 text-sm font-semibold text-white transition hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-700 focus:ring-offset-2 cursor-pointer">
              Reservation
            </button>

          </div>
        </div>
      </div>
    </div>

    <!-- Empty State -->
    <div v-if="!room || room.length === 0" class="py-16 text-center">
      <h2 class="text-xl font-bold text-gray-700">
        No rooms available
      </h2>
      <p class="mt-2 text-sm text-gray-500">
        Please check again later.
      </p>
    </div>

  </section>
</template>
