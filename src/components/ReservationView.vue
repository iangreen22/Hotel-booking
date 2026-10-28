<script>
export default {
    props: ['res2']
}
</script>

<template>
    <div class="p-8">
        <div class="h-30"></div>
        <h1 class="text-3xl font-bold mb-6">My Reservations</h1>

        <div  class="text-gray-500">No reservations yet.</div>

        <div v-for="booking in res2" :key="booking.id" class="border rounded-lg p-5 mb-4 bg-white shadow">

            <!-- <h2 class="text-xl font-bold">{{ booking.roomName }}</h2> -->

            <p>Guest: {{ booking.fullName }}</p>
            <p>Check-in: {{ booking.checkIn }}</p>
            <p>Check-out: {{ booking.checkOut }}</p>
            <p>Room: {{ booking.roomPrice }}</p>
            <p>Guests: {{ booking.guests }}</p>
            <p>Nights: {{ booking.totalNights }}</p>
            <p class="font-bold mt-2">Total: ₱ {{ booking.roomPrice * booking.totalNights }}</p>

            <p class="text-green-600 font-semibold mt-2">Confirmed</p>

        </div>

    </div>
</template>