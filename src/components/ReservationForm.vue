<script>
export default {
    emits: ['close'],

    data() {
        return {
            fullName: '',
            guests: '1',
            checkIn: '',
            checkOut: '',
            totalNights: 0
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
        }
    }
}
</script>


<template>

    <div class="fixed inset-0 bg-black/50">
        <div class="min-h-screen flex items-center justify-center px-4 py-4 mt-10">
            <div class="w-full max-w-4xl">
                <div class="bg-white rounded-xl shadow-lg overflow-hidden">
                    <!-- Header -->
                    <div class="bg-black border py-6 px-8 text-white flex justify-between">
                        <div class="flex justify-between items-center">
                            <div>
                                <h1 class="text-3xl font-bold">JIB HOTEL</h1>
                                <p class="text-blue-100">Luxury stays in the heart of the city</p>
                            </div>
                            <div class="text-4xl">
                                <i class="fas fa-hotel"></i>
                            </div>
                        </div>
                        <div>
                            <button @click="closeForm"
                                class="text-2xl font-semibold bg-white text-black cursor-pointer hover:scale-105 rounded-full px-5">X</button>
                        </div>
                    </div>

                    <!-- Booking Form -->
                    <form class="p-8 space-y-2">
                        <h2 class="text-2xl font-bold text-gray-800 border-b pb-2">Book Your Room</h2>

                        <!-- Guest Information -->
                        <div class="space-y-4">
                            <h3 class="text-lg font-semibold text-gray-700">Guest Information</h3>
                            <div class="grid md:grid-cols-2 gap-6">
                                <div>
                                    <label for="fullName" class="block text-sm font-medium text-gray-700 mb-1">Full
                                        Name</label>
                                    <input type="text" id="fullName" name="fullName" required
                                        class="w-full px-4 py-2 rounded-lg border border-gray-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
                                </div>
                                <div>
                                    <label for="guests" class="block text-sm font-medium text-gray-700 mb-1">Number
                                        of Guests</label>
                                    <select id="guests" name="guests" required
                                        class="w-full px-4 py-2 rounded-lg border border-gray-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
                                        <option value="1">1 Guest</option>
                                        <option value="2">2 Guests</option>
                                        <option value="3">3 Guests</option>
                                        <option value="4">4 Guests</option>
                                        <option value="4+">More than 4</option>
                                    </select>
                                </div>
                            </div>
                        </div>

                        <!-- Dates -->
                        <div class="space-y-4">
                            <h3 class="text-lg font-semibold text-gray-700">Stay Dates</h3>
                            <div class="grid grid-cols-2 gap-6">
                                <!-- Check-in Date -->
                                <div>
                                    <label for="checkIn" class="block text-sm font-medium text-gray-700 mb-1">
                                        Check-in Date
                                    </label>

                                    <input type="date" id="checkIn" v-model="checkIn"
                                        :min="new Date().toLocaleDateString('en-CA')" @change="calculateNights" required
                                        class="w-full px-4 py-2 rounded-lg border border-gray-300 focus:ring-2 focus:ring-blue-500">
                                </div>

                                <!-- Check-out Date -->
                                <div>
                                    <label for="checkOut" class="block text-sm font-medium text-gray-700 mb-1">
                                        Check-out Date
                                    </label>

                                    <input type="date" id="checkOut" v-model="checkOut"
                                        :min="checkIn || new Date().toLocaleDateString('en-CA')"
                                        @change="calculateNights" required
                                        class="w-full px-4 py-2 rounded-lg border border-gray-300 focus:ring-2 focus:ring-blue-500">
                                </div>
                            </div>
                        </div>

                        <!-- Stay Duration -->
                        <div v-if="checkIn && checkOut" class="mt-4 p-4 rounded-lg"
                            :class="totalNights > 0 ? 'bg-blue-50' : 'bg-red-50'">

                            <h3 class="text-lg font-bold text-gray-800">
                                Stay Summary
                            </h3>

                            <p v-if="totalNights > 0" class="text-blue-700 mt-2">
                                Check-in: {{ checkIn }}
                            </p>

                            <p v-if="totalNights > 0" class="text-blue-700">
                                Check-out: {{ checkOut }}
                            </p>

                            <p v-if="totalNights > 0" class="font-bold text-lg mt-2">
                                Total Stay: {{ totalNights }}
                                {{ totalNights === 1 ? 'night' : 'nights' }}
                            </p>

                            <p v-else class="text-red-600 font-medium">
                                Check-out must be later than check-in.
                            </p>
                        </div>

                        <!-- Payment and Submit -->
                        <div class="space-y-4">
                            <button type="submit"
                                class="w-full py-3 px-4 bg-black hover:bg-gray-950 cursor-pointer rounded-lg text-white font-bold text-lg shadow-md hover:shadow-lg transition duration-300">
                                <i class="fas fa-calendar-check mr-2"></i> Confirm Reservation
                            </button>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>