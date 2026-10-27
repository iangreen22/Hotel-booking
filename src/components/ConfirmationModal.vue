<script>
export default {
    props: ['toConfirm'],

    emits: ['confirm', 'close'],

    methods: {
        confirmBooking() {
            this.$emit('confirm')
        },

        closeModal() {
            this.$emit('close')
        }
    }
}
</script>

<template>
    <div class="fixed inset-0 z-[60] flex items-center justify-center bg-black/60 px-4 py-6" @click.self="closeModal">
        <div class="w-full max-w-md overflow-hidden rounded-2xl bg-white shadow-2xl">

            <!-- Header -->
            <div class="flex items-center justify-between bg-black px-6 py-5 text-white">
                <div>
                    <h2 class="text-2xl font-bold">JIB HOTEL</h2>
                    <p class="text-sm text-gray-300">Booking Confirmation</p>
                </div>

                <button type="button" @click="closeModal" class="text-2xl hover:text-gray-300">
                    &times;
                </button>
            </div>

            <!-- Confirmation Message -->
            <div class="px-6 pt-6 text-center">
                <div
                    class="mx-auto flex h-16 w-16 items-center justify-center rounded-full bg-green-100 text-3xl text-green-600">
                    ✓
                </div>

                <h3 class="mt-4 text-xl font-bold text-gray-800">
                    Review Your Reservation
                </h3>

                <p class="mt-1 text-sm text-gray-500">
                    Please check your booking details before confirming.
                </p>
            </div>

            <!-- Booking Details Card -->
            <div class="m-6 rounded-xl border border-gray-200 p-5">

                <div class="mb-4 border-b border-dashed border-gray-300 pb-4">
                    <p class="text-sm text-gray-500">Guest Name</p>
                    <p class="text-lg font-bold text-gray-800">
                        {{ toConfirm.fullName }}
                    </p>
                </div>

                <div class="space-y-4">

                    <div class="flex items-start justify-between gap-3">
                        <div>
                            <p class="text-sm text-gray-500">Check-in</p>
                            <p class="font-semibold text-gray-800">
                                {{ toConfirm.checkIn }}
                            </p>
                        </div>

                        <div class="text-right">
                            <p class="text-sm text-gray-500">Check-out</p>
                            <p class="font-semibold text-gray-800">
                                {{ toConfirm.checkOut }}
                            </p>
                        </div>
                    </div>

                    <div class="flex justify-between">
                        <span class="text-gray-500">Duration</span>
                        <span class="font-semibold text-gray-800">
                            {{ toConfirm.totalNights }}
                            {{ toConfirm.totalNights === 1 ? 'night' : 'nights' }}
                        </span>
                    </div>

                    <div class="flex justify-between">
                        <span class="text-gray-500">Room Price / Night</span>
                        <span class="font-semibold text-gray-800">
                            ₱{{ Number(toConfirm.roomPrice).toLocaleString('en-PH') }}
                        </span>
                    </div>

                </div>

                <!-- Total -->
                <div class="mt-5 flex items-center justify-between border-t border-dashed border-gray-300 pt-4">
                    <span class="font-bold text-black">Total Cost</span>

                    <span class="text-2xl font-bold text-black">
                        ₱{{ (toConfirm.totalNights * toConfirm.roomPrice).toLocaleString('en-PH') }}
                    </span>
                </div>
            </div>

            <!-- Buttons -->
            <div class="flex gap-3 px-6 pb-6">
                <button type="button" @click="closeModal"
                    class="flex-1 rounded-lg border border-gray-300 px-4 py-3 font-semibold text-gray-700 hover:bg-gray-100">
                    Go Back
                </button>

                <button type="button" @click="confirmBooking"
                    class="flex-1 rounded-lg bg-black px-4 py-3 font-semibold text-white transition hover:bg-gray-800">
                    Confirm Booking
                </button>
            </div>

        </div>
    </div>
</template>
