<script setup>
import { ref } from 'vue';
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Autoplay, Pagination } from 'swiper/modules';

import 'swiper/css';
import 'swiper/css/pagination';

const testimonials = ref([
    {
        id: 1,
        quote:
            "From start to finish, EVsleek made my EV journey effortless. Their team helped me choose the perfect car and installed a charger that looks as sleek as it performs. The design, the service, the speed—everything about EVsleek just feels premium. I love my new ride, and the support has been top-notch.",
        name: "Maya R.",
        location: "San Diego, CA",
        image: "/src/components/public/1.jpg",
        alt: "Maya R. with her Tesla",
    },
    {
        id: 2,
        quote:
            "Switching to an electric vehicle was a big decision, but EVsleek made it seamless. The home charger installation was quick and clean, and their advisors truly understood what I needed. I’ve never felt more confident in my car choice.",
        name: "James T.",
        location: "Austin, TX",
        image: "/src/components/public/adam1.jpg",
        alt: "James T. at his EV charging station",
    },
    {
        id: 3,
        quote:
            "The level of detail and care EVsleek puts into every step is unmatched. From the moment I walked in to the day my car arrived, everything was handled with professionalism and warmth. They didn’t just sell me a car—they gave me peace of mind.",
        name: "Lena K.",
        location: "Seattle, WA",
        image: "/src/components/public/3.jpg",
        alt: "Lena K. charging her EV at home",
    },
]);
</script>

<template>
    <section id="charging">
        <div class="max-w-6xl mx-auto px-4 py-12 md:py-20">
           
            
            <div class="text-center mb-10">
                <h1 class="text-2xl sm:text-3xl md:text-5xl font-bold text-gray-800 leading-tight">
                    DESIGNED FOR THE FUTURE.<br />
                    <span class="text-blue-600">BUILT FOR NOW.</span>
                </h1>
            </div>

            
            <div class="flex flex-col md:flex-row items-center gap-10 md:gap-12">
                <div class="relative w-full">
                    
                    <div class="relative rounded-lg overflow-hidden shadow-xl w-full">
                        <img src="/src/components/public/tesla-supercharger.jpg" alt="Electric Car Charging"
                            class="w-full h-auto object-cover" />
                    </div>

                    
                    <div class="absolute -bottom-20 left-6 hidden md:block w-52 h-60 overflow-hidden shadow-2xl"
                        style="clip-path: polygon(0% 0%, 80% 0%, 100% 20%, 100% 100%, 0% 100%)">
                        <img src="/src/components/public/char.jpg" alt="Smart Charging Station"
                            class="w-full h-full object-cover rounded-lg border-4 border-gray-200" />
                    </div>
                </div>
            </div>

            <div class="w-full max-w-xl mx-auto mt-12 md:mt-16 text-center md:text-left">
                <h2 class="text-2xl md:text-3xl font-bold text-gray-800">ELECTRIC VEHICLES</h2>
                <h3 class="text-xl md:text-2xl font-semibold text-gray-600">SMART CHARGING STATIONS</h3>
                <p class="text-gray-700 leading-relaxed mt-2">
                    Premium EVs from leading manufacturers, chosen for design, range, and smart technology.
                    Whether you're looking for luxury or efficiency, we've got the perfect electric match.
                </p>
            </div>

            
            <div class="py-16 bg-gray-100 mt-14 rounded-lg">
                <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center mb-12">
                    <h2 class="text-2xl md:text-3xl font-bold text-gray-900 uppercase tracking-tight">
                        What Our Customers Are Saying
                    </h2>
                </div>

                <swiper
                    :modules="[Autoplay, Pagination]"
                    :space-between="30"
                    :centered-slides="true"
                    :autoplay="{ delay: 4000, disableOnInteraction: false }"
                    :pagination="{ clickable: true }"
                    :loop="true"
                    class="max-w-4xl mx-auto px-4"
                >
                    <swiper-slide v-for="item in testimonials" :key="item.id">
                        <div class="flex flex-col md:flex-row gap-8 items-start text-center md:text-left">
                           
                            <div class="flex-1">
                                <blockquote class="text-gray-700 leading-relaxed text-lg md:text-2xl italic">
                                    "{{ item.quote }}"
                                </blockquote>
                                <div class="mt-6">
                                    <p class="font-semibold text-gray-900">{{ item.name }}</p>
                                    <p class="text-sm text-gray-500">{{ item.location }}</p>
                                </div>
                            </div>

                            
                            <div class="w-full md:w-64 h-64 rounded-xl overflow-hidden shadow-lg border border-gray-200">
                                <img :src="item.image" :alt="item.alt" class="w-full h-full object-cover" />
                            </div>
                        </div>
                    </swiper-slide>
                </swiper>
            </div>
        </div>
    </section>
</template>
