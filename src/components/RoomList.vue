<script>

export default {
    props:['roomData'],
    data() {
        return {
            roomType: 'All',
            guests: 1,
            maxPrice: 300,
            selectedRoom: null
        }
    },

    methods: {
        checkRoom(room) {
            if (this.roomType != 'All' && room.type != this.roomType) {
                return false
            }

            if (room.capacity < this.guests) {
                return false
            }

            if (room.price > this.maxPrice) {
                return false
            }

            return true
        },

        showRoom(room) {
            this.selectedRoom = room
        },

        closeRoom() {
            this.selectedRoom = null
        },

        bookRoom(room) {
            this.$emit('bookRoom', room)
        }
    }
}
</script>

<template>
   <div class="mt-20 sm:mt-24 lg:mt-30 mx-4 sm:mx-6 lg:mx-10 xl:mx-15">

    <!-- Section Title -->
    <h1 class="text-2xl sm:text-3xl lg:text-4xl font-bold mb-5">
        Our Rooms
    </h1>

    <!-- Filters -->
    <div class="flex flex-col sm:flex-row sm:flex-wrap 
                sm:items-end gap-4 sm:gap-5 mb-6">

        <!-- Room Type -->
        <div class="w-full sm:w-48">
            <label class="block text-sm font-medium mb-2">
                Room Type
            </label>

            <select
                v-model="roomType"
                class="w-full border border-gray-300 p-3 rounded-lg
                       outline-none focus:ring-2 focus:ring-gray-500
                       bg-white"
            >
                <option>All</option>
                <option>Standard</option>
                <option>Deluxe</option>
                <option>Suite</option>
            </select>
        </div>

        <!-- Number of Guests -->
        <div class="w-full sm:w-48">
            <label class="block text-sm font-medium mb-2">
                Guests
            </label>

            <select
                v-model.number="guests"
                class="w-full border border-gray-300 p-3 rounded-lg
                       outline-none focus:ring-2 focus:ring-gray-500
                       bg-white"
            >
                <option :value="1">1 Guest</option>
                <option :value="2">2 Guests</option>
                <option :value="3">3 Guests</option>
                <option :value="4">4 Guests</option>
                <option :value="5">5 Guests</option>
            </select>
        </div>

        <!-- Maximum Price -->
        <div class="w-full sm:flex-1 sm:min-w-48 sm:max-w-80">

            <div class="flex items-center justify-between gap-3 mb-2">
                <label class="text-sm font-medium">
                    Maximum Price
                </label>

                <span class="font-semibold text-sm whitespace-nowrap">
                    ₱{{ maxPrice.toLocaleString('en-PH') }}
                </span>
            </div>

            <input
                type="range"
                v-model.number="maxPrice"
                min="1000"
                max="5000"
                step="5"
                class="w-full cursor-pointer accent-[#302218]"
            />

            <div class="flex justify-between text-xs text-gray-500 mt-1">
                <span>₱1,000</span>
                <span>₱5,000</span>
            </div>

        </div>

    </div>

</div>
</template>