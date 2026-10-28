<script>
import Navbar from './components/Navbar.vue';
import HomeView from './components/HomeView.vue';
import AboutView from './components/AboutView.vue';
import ContactView from './components/ContactView.vue';
import Footer from './components/Footer.vue';
import Services from './components/Services.vue';
import RoomList from './components/RoomList.vue';
import RoomCard from './components/RoomCard.vue';
import RoomModal from './components/RoomModal.vue';
import ReservationForm from './components/ReservationForm.vue';
import ReservationView from './components/ReservationView.vue';
import ConfirmationModal from './components/ConfirmationModal.vue';


export default {
    components: {
        Navbar, HomeView, AboutView, ContactView, Footer, Services, RoomList, RoomCard, RoomModal, ReservationForm, ReservationView, ConfirmationModal
    },
    data() {
        return {
            rooms: [
                {
                    id: 1,
                    name: 'Deluxe Suite',
                    type: 'Suite',
                    price: 195,
                    capacity: 4,
                    image: 'https://i.pinimg.com/736x/89/2e/a0/892ea0095c64f9ca3e5578bfc77faf3c.jpg',
                    amenities: 'WiFi, Aircon, TV, Breakfast'
                },
                {
                    id: 2,
                    name: 'Deluxe Room',
                    type: 'Deluxe',
                    price: 125,
                    capacity: 2,
                    image: 'https://i.pinimg.com/1200x/95/dc/ed/95dced36ebd93d4ce37933994a63fa20.jpg',
                    amenities: 'WiFi, Aircon, TV'
                },
                {
                    id: 3,
                    name: 'Standard Room',
                    type: 'Standard',
                    price: 95,
                    capacity: 2,
                    image: 'https://i.pinimg.com/1200x/99/66/d3/9966d3a090a385e078aeefca30ef9465.jpg',
                    amenities: 'WiFi, Aircon'
                },
                {
                    id: 4,
                    name: 'Family Suite',
                    type: 'Suite',
                    price: 220,
                    capacity: 5,
                    image: 'https://i.pinimg.com/1200x/2c/20/68/2c2068977745bed2fa04faf971696df4.jpg',
                    amenities: 'WiFi, Aircon, TV, Breakfast'
                },
                {
                    id: 5,
                    name: 'Twin Room',
                    type: 'Standard',
                    price: 110,
                    capacity: 2,
                    image: 'https://i.pinimg.com/736x/a5/85/66/a585664f7436275f126faebcf9fc49b4.jpg',
                    amenities: 'WiFi, TV'
                },
                {
                    id: 6,
                    name: 'Executive Room',
                    type: 'Deluxe',
                    price: 165,
                    capacity: 3,
                    image: 'https://i.pinimg.com/736x/5d/7d/76/5d7d7682b55ad24642df5b72b899cd0e.jpg',
                    amenities: 'WiFi, Aircon, TV, Mini Bar'
                }
            ],
            page: 'home',
            showModal: [],
            formInfo: [],
            showConfirmModal: [],
            reservePage: [],
            modalCard: false,
            form: false,
            confirm: false

        }
    },
    methods: {
        showHome(i) {
            this.page = i;
        },

        showDetails(name, type, price, capacity, image, amenities){
            this.showModal.push({...name,...type,...price, ...capacity, ...image, ...amenities});
            this.modalCard = true;  
        }, 

        showForm(fullName,guests, checkIn, checkOut){
            this.formInfo.push({...fullName,...guests, ...checkIn, ...checkOut})
            this.form = true;
        },

        showConfirmForm(fullName,guests, checkIn, checkOut, totalNights,roomPrice, totalCost){
            this.showConfirmModal.push({...fullName,...guests, ...checkIn, ...checkOut, ...totalNights,...roomPrice, ...totalCost})
            this.confirm = true;
            this.form = false;
        },

        finalConfirmation(fullName,guests, checkIn, checkOut, totalNights,roomPrice, totalCost){
            this.reservePage.push({...fullName,...guests, ...checkIn, ...checkOut, ...totalNights,...roomPrice, ...totalCost})
            this.confirm = false;
            this.showConfirmModal = [];
            alert("successfully book!")
        },

        closeModal(){
            this.modalCard = false;
            this.form = false;
            this.confirm = false;
            this.showModal = [];
        }

    }

}

</script>


<template>
    <Navbar @go-home="showHome" />
    <HomeView v-if="page === 'home'"  @go-home="showHome" />
    <AboutView v-if="page === 'about'" />
    <Services v-if="page === 'services'" />
    <RoomList v-if="page === 'roomlist'" />
    <RoomCard v-if="page === 'roomlist'" :room="rooms" @toRoom="showDetails" @bookRoom="showForm"/>
    <RoomModal v-if="modalCard" :modal="showModal" @close="closeModal"/>
    <ContactView v-if="page === 'contact'" />
    <ReservationView v-if="page === 'res'"  :res2="reservePage"/>
    <ReservationForm v-if="form" @close="closeModal" :toForm="showModal" @goConfirm="showConfirmForm"/>
    <ConfirmationModal v-if="confirm" :toConfirm="showConfirmModal" @close="closeModal" @goConfirm="finalConfirmation"/>
    <Footer />
</template>
