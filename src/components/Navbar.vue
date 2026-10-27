<script>
export default {
    emits: ['go-home'],
    data() {
        return {}
    },
    methods: {
        menu(page) {
            this.$emit('go-home', page)
        }
    }
}
</script>
<template>

    <header class="fixed top-0 left-0 z-50 w-full">
  
        <nav class="mx-auto flex h-24 max-w-[1600px] items-center justify-between px-5 sm:px-8 lg:px-12 bg-black/50 backdrop-blur-md"
            aria-label="Main navigation">
            <a href="#"
                class="group flex items-center gap-3 focus:outline-none focus-visible:ring-2 focus-visible:ring-lime-400 focus-visible:ring-offset-2 rounded-lg">
                <img src="../assets/logo.png" alt="" class="h-[100px] w-[100px]">


            </a>

            <ul class="hidden items-center gap-10 lg:flex">
                <li>
                    <a @click="menu('home')" href="#" aria-current="page"
                        class="text-sm font-bold uppercase tracking-[0.08em] text-white hover:border-b hover:border-white ">
                        HOME
            
                    </a>
                </li>
                <li>
                    <a @click="menu('about')" href="#"
                        class="text-sm font-bold uppercase tracking-[0.08em] text-white hover:border-b hover:border-white ">
                        ABOUT
                    </a>
                </li>
                <li>
                    <a @click="menu('services')" href="#"
                        class="text-sm font-bold uppercase tracking-[0.08em] text-white hover:border-b hover:border-white ">
                        SERVICES
                    </a>
                </li>
                <li>
                    <a @click="menu('roomlist')" href="#"
                        class="text-sm font-bold uppercase tracking-[0.08em] text-white hover:border-b hover:border-white ">
                        ROOMS
                    </a>
                </li>
                
            
                <li>
                    <a @click="menu('contact')" href="#"
                        class="text-sm font-bold uppercase tracking-[0.08em] text-white hover:border-b hover:border-white ">
                        Contact
                    </a>
                </li>

            </ul>

            <div class="flex items-center gap-4">
                <a href="#" @click="menu('res')"
                    class="group relative hidden items-center gap-2.5 overflow-hidden rounded-full border-stone-950 px-6 py-3 text-sm font-bold uppercase tracking-[0.06em] text-white transition-colors duration-300 hover:text-stone-950 lg:inline-flex">
                    <span
                        class="text-white absolute inset-0 -translate-x-full bg-white transition-transform duration-300 ease-out group-hover:translate-x-0"></span>
                    <span  class="relative">My Reservation</span>
                    <svg class="relative h-4 w-4 transition-transform duration-300 group-hover:translate-x-1"
                        fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3" />
                    </svg>
                </a>
            </div>
        </nav>
    
    </header>
</template>