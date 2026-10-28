<script>
export default {
    emits: ['go-home'],

    data() {
        return {
            mobileMenuOpen: false
        }
    },

    methods: {
        menu(page) {
            this.$emit('go-home', page)
            this.mobileMenuOpen = false
        },

        toggleMenu() {
            this.mobileMenuOpen = !this.mobileMenuOpen
        }
    }
}
</script>

<template>
    <header class="fixed top-0 left-0 z-50 w-full">

        <nav class="mx-auto flex h-20 sm:h-24 max-w-[1600px] items-center justify-between bg-black/60 px-4 sm:px-8 lg:px-12 backdrop-blur-md"
            aria-label="Main navigation">

            <a href="#" @click.prevent="menu('home')"
                class="flex shrink-0 items-center rounded-lg focus:outline-none focus-visible:ring-2 focus-visible:ring-lime-400"
                aria-label="JIB Hotel home">
                <img src="../assets/logo.png" alt="JIB Hotel"
                    class="h-16 w-16 object-contain sm:h-20 sm:w-20 lg:h-24 lg:w-24" />
            </a>


            <ul class="hidden items-center gap-6 xl:gap-10 lg:flex">
                <li>
                    <a href="#" @click.prevent="menu('home')" aria-current="page"
                        class="text-sm font-bold uppercase tracking-wider text-white transition-colors hover:text-lime-300">
                        Home
                    </a>
                </li>

                <li>
                    <a href="#" @click.prevent="menu('about')"
                        class="text-sm font-bold uppercase tracking-wider text-white transition-colors hover:text-lime-300">
                        About
                    </a>
                </li>

                <li>
                    <a href="#" @click.prevent="menu('services')"
                        class="text-sm font-bold uppercase tracking-wider text-white transition-colors hover:text-lime-300">
                        Services
                    </a>
                </li>

                <li>
                    <a href="#" @click.prevent="menu('roomlist')"
                        class="text-sm font-bold uppercase tracking-wider text-white transition-colors hover:text-lime-300">
                        Rooms
                    </a>
                </li>

                <li>
                    <a href="#" @click.prevent="menu('contact')"
                        class="text-sm font-bold uppercase tracking-wider text-white transition-colors hover:text-lime-300">
                        Contact
                    </a>
                </li>
            </ul>


            <div class="flex shrink-0 items-center gap-3">

                <a href="#" @click.prevent="menu('res')"
                    class="group relative hidden items-center gap-2 overflow-hidden rounded-full border border-white/70 px-5 py-3 text-xs font-bold uppercase tracking-wider text-white transition-colors duration-300 hover:text-black lg:inline-flex xl:px-6 xl:text-sm">
                    <span
                        class="absolute inset-0 -translate-x-full bg-white transition-transform duration-300 ease-out group-hover:translate-x-0"></span>

                    <span class="relative">My Reservation</span>

                    <svg class="relative h-4 w-4 transition-transform duration-300 group-hover:translate-x-1"
                        fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5" aria-hidden="true">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3" />
                    </svg>
                </a>


                <button type="button" @click="toggleMenu"
                    class="inline-flex h-11 w-11 items-center justify-center rounded-lg text-white transition hover:bg-white/10 focus:outline-none focus-visible:ring-2 focus-visible:ring-lime-300 lg:hidden"
                    :aria-expanded="mobileMenuOpen" aria-controls="mobile-navigation"
                    :aria-label="mobileMenuOpen ? 'Close navigation menu' : 'Open navigation menu'">
                    <svg v-if="!mobileMenuOpen" class="h-7 w-7" fill="none" viewBox="0 0 24 24" stroke="currentColor"
                        stroke-width="2" aria-hidden="true">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
                    </svg>

                    <svg v-else class="h-7 w-7" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"
                        aria-hidden="true">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>
            </div>
        </nav>


        <div v-if="mobileMenuOpen" id="mobile-navigation"
            class="border-t border-white/10 bg-black/95 px-5 pb-6 pt-3 shadow-xl backdrop-blur-md lg:hidden">
            <ul class="mx-auto flex max-w-lg flex-col">

                <li>
                    <a href="#" @click.prevent="menu('home')"
                        class="block rounded-lg px-4 py-3 text-sm font-bold uppercase tracking-wider text-white transition hover:bg-white/10 hover:text-lime-300">
                        Home
                    </a>
                </li>

                <li>
                    <a href="#" @click.prevent="menu('about')"
                        class="block rounded-lg px-4 py-3 text-sm font-bold uppercase tracking-wider text-white transition hover:bg-white/10 hover:text-lime-300">
                        About
                    </a>
                </li>

                <li>
                    <a href="#" @click.prevent="menu('services')"
                        class="block rounded-lg px-4 py-3 text-sm font-bold uppercase tracking-wider text-white transition hover:bg-white/10 hover:text-lime-300">
                        Services
                    </a>
                </li>

                <li>
                    <a href="#" @click.prevent="menu('roomlist')"
                        class="block rounded-lg px-4 py-3 text-sm font-bold uppercase tracking-wider text-white transition hover:bg-white/10 hover:text-lime-300">
                        Rooms
                    </a>
                </li>

                <li>
                    <a href="#" @click.prevent="menu('contact')"
                        class="block rounded-lg px-4 py-3 text-sm font-bold uppercase tracking-wider text-white transition hover:bg-white/10 hover:text-lime-300">
                        Contact
                    </a>
                </li>


                <li class="mt-3 border-t border-white/20 pt-4">
                    <a href="#" @click.prevent="menu('res')"
                        class="flex w-full items-center justify-center gap-3 rounded-full border border-white px-5 py-3 text-sm font-bold uppercase tracking-wider text-white transition hover:bg-white hover:text-black">
                        My Reservation

                        <svg class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"
                            aria-hidden="true">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3" />
                        </svg>
                    </a>
                </li>

            </ul>
        </div>

    </header>
</template>
