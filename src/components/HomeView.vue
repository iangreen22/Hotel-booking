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
    <section class="min-h-screen flex items-center bg-cover bg-center"
        style="background-image: linear-gradient(rgba(0,0,0,0.65), rgba(0,0,0,0.75)), url('https://plus.unsplash.com/premium_photo-1661929519129-7a76946c1d38?q=80&w=1074&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=NHwxMjA3fDA%3D');">

        <div class="max-w-7xl mx-auto px-6 py-24 w-full">

            <p class="uppercase tracking-[5px] text-zinc-300 mb-5">
                Luxury • Comfort • Experience
            </p>

            <h1 class="text-5xl md:text-7xl font-bold max-w-3xl leading-tight text-white">
                Your Perfect Stay Starts Here.
            </h1>

            <p class="text-zinc-300 mt-6 max-w-xl leading-7">
                Experience modern luxury, relaxing rooms, and
                exceptional hospitality at JIB's Hotel.
            </p>

            <div class="flex flex-col sm:flex-row items-stretch sm:items-center gap-3 sm:gap-5 w-full">


                <a @click="menu('roomlist')" href="#rooms"
                    class="flex items-center justify-center w-full sm:w-auto mt-4 sm:mt-8 px-5 sm:px-8 py-3 bg-white text-black rounded-md font-semibold text-sm sm:text-base text-center hover:bg-zinc-300 transition duration-300 cursor-pointer">
                    Explore Our Rooms
                </a>

                <!-- Search Bar -->
                <div
                    class="flex items-stretch w-full sm:w-auto sm:min-w-0 mt-0 sm:mt-8 bg-white rounded-md font-semibold transition">
                    <input type="text" placeholder="Search available rooms"
                        class="min-w-0 flex-1 px-3 py-3 border border-zinc-500 rounded-l-md outline-none text-sm text-black placeholder:text-xs sm:placeholder:text-sm placeholder:text-zinc-500 placeholder:italic font-normal focus:border-black" />

                    <button type="button"
                        class="shrink-0 px-4 sm:px-5 py-3 bg-white text-black border border-l-0 border-zinc-500 rounded-r-md text-sm sm:text-base hover:bg-zinc-300 transition duration-300 cursor-pointer">
                        Search
                    </button>
                </div>

            </div>
        </div>
    </section>

    <div class="w-full flex flex-col md:flex-row py-24">
        <div class="flex flex-col w-[90%] lg:w-4/5 2xl:w-3/5 mx-auto">
            <div class="w-full md:w-4/5 md:mx-auto text-center pt-3 px-4 md:!px-0 text-center">
                <h1 class="text-3xl mt-2 md:text-4xl font-semibold text-gray-800">
                    Our <span class="text-emerald-600"> Featured</span> Rooms
                </h1>

            </div>
            <div class="flex flex-col md:flex-row w-full">
                <div class="basis-1/3 w-full border border-gray-100 dark:!border-gray-600 rounded-md pr-0 md:mr-4 mt-6">
                    <div class="flex flex-col relative">
                        <!-- Image (c) by: https://unsplash.com/de/@vojtechbruzek -->
                        <img src="https://images.unsplash.com/photo-1618773928121-c32242e63f39?q=80&w=2670&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
                            class="w-full relative z-10 max-h-80" title="" alt="" />
                        <div class="absolute z-20 bg-emerald-600 uppercase px-3 py-1 top-3 right-3 text-white text-sm">
                            Wifi — TV (Cable)</div>
                    </div>
                    <div class="flex flex-col px-4">
                        <p class="text-sm mt-3 text-gray-300 dark:text-gray-600 font-semibold">
                            Saison room
                        </p>
                        <h1 class="text-2xl my-2 md:text-3xl font-bold text-gray-600 ">
                            <span class="text-emerald-600">Single</span> room
                        </h1>
                        <p class="text-sm mb-3 line-clamp-3 hover:line-clamp-none text-gray-500 ">
                            You have the option of canceling by 6 pm on the day of arrival. Dogs must be requested
                            in
                            advance. The max lines is set to three and all over are invisible. Hover with your mouse
                            or
                            push with a finger on your mobile device on the text to show all lines.
                        </p>
                    </div>
                    <div class="flex flex-row py-3 px-4 border-t border-gray-100 dark:!border-gray-600">
                        <div class="w-1/2 flex flex-row dark:text-gray-400">
                            <span class="mr-1">$</span>
                            <span>89.00 ¬ Night</span>
                        </div>
                        <div class="w-1/2 text-yellow-400 text-right font-semibold">
                            ☆☆☆☆<span class="text-gray-500 font-normal">☆</span>
                        </div>
                    </div>
                </div>
                <div class="basis-1/3 w-full border border-gray-100 dark:!border-gray-600 rounded-md pr-0 md:mx-4 mt-6">
                    <div class="flex flex-col relative">
                        <!-- Image (c) by: https://unsplash.com/de/@vojtechbruzek -->
                        <img src="https://images.unsplash.com/photo-1618773928121-c32242e63f39?q=80&w=2670&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
                            class="w-full relative z-10 max-h-80" title="" alt="" />
                        <div class="absolute z-20 bg-emerald-600 uppercase px-3 py-1 top-3 right-3 text-white text-sm">
                            Wifi — TV (Cable)</div>
                    </div>
                    <div class="flex flex-col px-4">
                        <p class="text-sm mt-3 text-gray-300 dark:text-gray-600 font-semibold">
                            Saison room
                        </p>
                        <h1 class="text-2xl my-2 md:text-3xl font-bold text-gray-600 ">
                            <span class="text-emerald-600">Love</span> Suite
                        </h1>
                        <p class="text-sm mb-3 line-clamp-3 hover:line-clamp-none text-gray-500 ">
                            In this suite there is a double bed and a bottle of sparkling wine on request at
                            check-in.
                            The max lines is set to three and all over are invisible. Hover with your mouse or push
                            with
                            a finger on your mobile device on the text to show all lines.
                        </p>
                    </div>
                    <div class="flex flex-row py-3 px-4 border-t border-gray-100 dark:!border-gray-600">
                        <div class="basis-1/2 flex flex-row dark:text-gray-400">
                            <span class="mr-1">$</span>
                            <span>119.00 ¬ Night</span>
                        </div>
                        <div class="basis-1/2 text-yellow-400 text-end font-semibold">
                            ☆☆☆<span class="text-gray-500 font-normal">☆☆</span>
                        </div>
                    </div>
                </div>
                <div class="basis-1/3 w-full border border-gray-100 dark:!border-gray-600 rounded-md pr-0 md:ml-4 mt-6">
                    <div class="flex flex-col relative">
                        <!-- Image (c) by: https://unsplash.com/de/@vojtechbruzek -->
                        <img src="https://images.unsplash.com/photo-1618773928121-c32242e63f39?q=80&w=2670&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
                            class="w-full relative z-10 max-h-80" title="" alt="" />
                        <div class="absolute z-20 bg-emerald-600 uppercase px-3 py-1 top-3 right-3 text-white text-sm">
                            Wifi — TV (Sky)</div>
                    </div>
                    <div class="flex flex-col px-4">
                        <p class="text-sm mt-3 text-gray-300 dark:text-gray-600 font-semibold">
                            Premium room
                        </p>
                        <h1 class="text-2xl my-2 md:text-3xl font-bold text-gray-600 ">
                            <span class="text-emerald-600">Individual</span> room
                        </h1>
                        <p class="text-sm mb-3 line-clamp-3 hover:line-clamp-none text-gray-500 ">
                            We add up to two more beds. Crib possible. Breakfast must be ordered <u>separately</u>.
                            The
                            max lines is set to three and all over are invisible. Hover with your mouse or push with
                            a
                            finger on your mobile device on the text to show all lines.
                        </p>
                    </div>
                    <div class="flex flex-row py-3 px-4 border-t border-gray-100 dark:!border-gray-600">
                        <div class="w-1/2 flex flex-row dark:text-gray-400">
                            <span class="mr-1">$</span>
                            <span>149.00 ¬ Night</span>
                        </div>
                        <div class="w-1/2 text-yellow-400 text-end font-semibold">
                            ☆☆☆☆☆
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>



</template>