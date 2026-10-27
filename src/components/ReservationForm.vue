<script>
export default {
    data() {
        return {

        }
    },

    methods: {
        closeForm() {
            this.$emit('close')
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
                            <div class="grid md:grid-cols-2 gap-6">
                                <div>
                                    <label for="checkIn" class="block text-sm font-medium text-gray-700 mb-1">Check-in
                                        Date</label>
                                    <input type="date" id="checkIn" name="checkIn" required
                                        class="w-full px-4 py-2 rounded-lg border border-gray-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
                                </div>
                                <div>
                                    <label for="checkOut" class="block text-sm font-medium text-gray-700 mb-1">Check-out
                                        Date</label>
                                    <input type="date" id="checkOut" name="checkOut" required
                                        class="w-full px-4 py-2 rounded-lg border border-gray-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
                                </div>
                            </div>
                        </div>
                        <!-- Payment and Submit -->
                        <div class="space-y-4">
                            <button type="submit"
                                class="w-full py-3 px-4 bg-black hover:bg-gray-950 cursor-pointer rounded-lg text-white font-bold text-lg shadow-md hover:shadow-lg transition duration-300">
                                <i class="fas fa-calendar-check mr-2"></i> Confirm Booking
                            </button>
                        </div>
                    </form>

                    <!-- Footer -->
                    <div class="bg-gray-50 px-8 py-4 border-t">
                        <div class="flex flex-col md:flex-row justify-between items-center">
                            <div class="text-sm text-gray-600 mb-2 md:mb-0">
                                <i class="fas fa-phone-alt mr-1"></i> +63 951 073 9405
                            </div>
                            <div class="text-sm text-gray-600 mb-2 md:mb-0">
                                <i class="fas fa-envelope mr-1"></i> reservations@jibhotel.com
                            </div>
                            <div class="text-sm text-gray-600">
                                <i class="fas fa-map-marker-alt mr-1"></i> San Miguel, Tagum City
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>