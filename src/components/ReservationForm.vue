<script>
export default {
    emits: ['close', 'goConfirm'],

    data() {
        return {
            fullName: '',
            guests: 1,
            checkIn: '',
            checkOut: '',
            totalNights: 0,
            roomPrice: 2500
        }
    },

    methods: {
        closeForm() {
            this.$emit('close')
        },

        calculateNights() {
            if (!this.checkIn || !this.checkOut) {
                this.totalNights = 0
                return
            }

            const checkInDate = new Date(this.checkIn)
            const checkOutDate = new Date(this.checkOut)

            const difference = checkOutDate - checkInDate

            this.totalNights = difference / (1000 * 60 * 60 * 24)

            if (this.totalNights <= 0) {
                this.totalNights = 0
            }
        },

        toConfirm() {
            if (this.totalNights <= 0) {
                return
            }

            this.$emit('goConfirm', {
                fullName: this.fullName,
                guests: this.guests,
                checkIn: this.checkIn,
                checkOut: this.checkOut,
                totalNights: this.totalNights,
                roomPrice: this.roomPrice,
                totalCost: this.totalNights * this.roomPrice
            })
        }
    }
}
</script>

<template>
    <div class="fixed inset-0 z-50 flex items-center justify-center bg-black/50 px-4">

        <div class="w-full max-w-lg overflow-hidden rounded-xl bg-white shadow-xl">

            <!-- Header -->
            <div class="flex items-center justify-between bg-black px-6 py-5 text-white">
                <div>
                    <h1 class="text-2xl font-bold">JIB HOTEL</h1>
                    <p class="text-sm text-gray-300">Room Reservation</p>
                </div>

                <button @click="closeForm" type="button" class="rounded-full px-3 py-1 text-xl hover:bg-gray-700">
                    &times;
                </button>
            </div>

            <!-- Reservation Form -->
            <form @submit.prevent="toConfirm" class="space-y-5 p-6">
                <div class="grid grid-cols-2 gap-3">
                    <!-- Full Name -->
                    <div>
                        <label class="mb-2 block font-semibold text-gray-700">
                            Full Name
                        </label>

                        <input v-model="fullName" type="text" placeholder="Enter your full name" required
                            class="w-full rounded-lg border border-gray-300 px-4 py-3 outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100">
                    </div>

                    <!-- Number of Guests -->
                    <div>
                        <label class="mb-2 block font-semibold text-gray-700">
                            Number of Guests
                        </label>

                        <input v-model.number="guests" type="number" min="1" max="10" required
                            class="w-full rounded-lg border border-gray-300 px-4 py-3 outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100">

                        <p class="mt-1 text-sm text-gray-500">
                            Enter the number of guests (1–10).
                        </p>
                    </div>
                    <!-- Check-in -->
                    <div>
                        <label class="mb-2 block font-semibold text-gray-700">
                            Check-in Date
                        </label>

                        <input v-model="checkIn" @change="calculateNights" type="date"
                            :min="new Date().toLocaleDateString('en-CA')" required
                            class="w-full rounded-lg border border-gray-300 px-4 py-3 outline-none focus:border-blue-500">
                    </div>

                    <!-- Check-out -->
                    <div>
                        <label class="mb-2 block font-semibold text-gray-700">
                            Check-out Date
                        </label>

                        <input v-model="checkOut" @change="calculateNights" type="date"
                            :min="checkIn || new Date().toLocaleDateString('en-CA')" required
                            class="w-full rounded-lg border border-gray-300 px-4 py-3 outline-none focus:border-blue-500">
                    </div>
                </div>

                <!-- Total Cost -->
                <div class="rounded-lg bg-gray-100 p-5">

                    <div class="flex justify-between text-gray-600">
                        <span>Room Price / Night</span>
                        <span>₱{{ roomPrice.toLocaleString() }}</span>
                    </div>

                    <div class="mt-3 flex justify-between text-gray-600">
                        <span>Number of Guests</span>
                        <span>{{ guests }}</span>
                    </div>

                    <div class="mt-3 flex justify-between text-gray-600">
                        <span>Total Nights</span>
                        <span>{{ totalNights }}</span>
                    </div>

                    <div class="mt-4 flex justify-between border-t border-gray-300 pt-4">
                        <span class="text-lg font-bold text-black">
                            Total Cost
                        </span>

                        <span class="text-2xl font-bold text-black">
                            ₱{{ (totalNights * roomPrice).toLocaleString() }}
                        </span>
                    </div>

                    <p v-if="checkIn && checkOut && totalNights === 0" class="mt-3 text-sm text-red-600">
                        Check-out must be later than check-in.
                    </p>
                </div>

                <!-- Confirm Button -->
                <button @click="toConfirm(fullName, guests, checkIn, checkOut, totalNights, roomPrice, totalNights * roomPrice)" type="submit" :disabled="totalNights <= 0 || guests < 1 || guests > 10"
                    class="w-full rounded-lg bg-black py-3 font-bold text-white transition hover:bg-gray-800 disabled:cursor-not-allowed disabled:opacity-50">
                    Confirm Reservation
                </button>

            </form>
        </div>
    </div>
</template>
