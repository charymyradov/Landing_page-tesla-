<script setup>
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Autoplay, Pagination, Navigation } from 'swiper/modules';

// Swiper CSS
import 'swiper/css';
import 'swiper/css/pagination';
import 'swiper/css/navigation';
</script>

<template>
  <section id="discover">
    <!-- Swiper: Solar & Powerwall Ürünleri -->
    <div class="w-full h-64 sm:h-80 md:h-96 px-4 sm:px-10 lg:px-20">
      <swiper
        :modules="[Autoplay, Pagination, Navigation]"
        :slides-per-view="1.1"
        :space-between="16"
        :centered-slides="true"
        :loop="true"
        :breakpoints="{
          640: { slidesPerView: 1.5, spaceBetween: 20 },
          768: { slidesPerView: 2.2, spaceBetween: 20 },
          1024: { slidesPerView: 3, spaceBetween: 24 }
        }"
        :navigation="true"
        :pagination="{ clickable: true }"
        :autoplay="{ delay: 4000, disableOnInteraction: false }"
        class="h-full"
      >
        <!-- Slide 1 -->
        <swiper-slide>
          <div
            class="relative rounded-2xl overflow-hidden h-full flex items-end bg-cover bg-center"
            :style="{ backgroundImage: 'url(/src/components/public/D_PW.jpg)' }"
          >
            <div class="bg-black/50 text-white p-4 sm:p-6 w-full">
              <h2 class="text-xl sm:text-2xl font-bold">Powerwall</h2>
              <p class="text-xs sm:text-sm mt-2">Keep Your Lights On During Outages</p>
              <div class="flex flex-wrap gap-3 mt-4">
                <button class="px-4 py-2 rounded-lg bg-blue-600 text-white font-semibold hover:bg-blue-700">
                  Order Now
                </button>
                <button class="px-4 py-2 rounded-lg bg-white text-gray-900 font-semibold hover:bg-gray-200">
                  Learn More
                </button>
              </div>
            </div>
          </div>
        </swiper-slide>

        <!-- Slide 2 -->
        <swiper-slide>
          <div
            class="relative rounded-2xl overflow-hidden h-full flex items-end bg-cover bg-center"
            :style="{ backgroundImage: 'url(/src/components/public/solar-roof.jpg)' }"
          >
            <div class="bg-black/50 text-white p-4 sm:p-6 w-full">
              <h2 class="text-xl sm:text-2xl font-bold">Solar Roof</h2>
              <p class="text-xs sm:text-sm mt-2">Generate Clean Energy From Your Roof</p>
              <div class="flex flex-wrap gap-3 mt-4">
                <button class="px-4 py-2 rounded-lg bg-blue-600 text-white font-semibold hover:bg-blue-700">
                  Order Now
                </button>
                <button class="px-4 py-2 rounded-lg bg-white text-gray-900 font-semibold hover:bg-gray-200">
                  Learn More
                </button>
              </div>
            </div>
          </div>
        </swiper-slide>

        <!-- Slide 3 -->
        <swiper-slide>
          <div
            class="relative rounded-2xl overflow-hidden h-full flex items-end bg-cover bg-center"
            :style="{ backgroundImage: 'url(/src/components/public/solar-panels.png)' }"
          >
            <div class="bg-black/50 text-white p-4 sm:p-6 w-full">
              <h2 class="text-xl sm:text-2xl font-bold">Solar Panels</h2>
              <p class="text-xs sm:text-sm mt-2">Efficient, Affordable Solar for Your Home</p>
              <div class="flex flex-wrap gap-3 mt-4">
                <button class="px-4 py-2 rounded-lg bg-blue-600 text-white font-semibold hover:bg-blue-700">
                  Order Now
                </button>
                <button class="px-4 py-2 rounded-lg bg-white text-gray-900 font-semibold hover:bg-gray-200">
                  Learn More
                </button>
              </div>
            </div>
          </div>
        </swiper-slide>

        <!-- Slide 4 -->
        <swiper-slide>
          <div
            class="relative rounded-2xl overflow-hidden h-full flex items-end bg-cover bg-center"
            :style="{ backgroundImage: 'url(/src/components/public/tesla-hornsdale.png)' }"
          >
            <div class="bg-black/50 text-white p-4 sm:p-6 w-full">
              <h2 class="text-xl sm:text-2xl font-bold">Powerwall</h2>
              <p class="text-xs sm:text-sm mt-2">Keep Your Lights On During Outages</p>
              <div class="flex flex-wrap gap-3 mt-4">
                <button class="px-4 py-2 rounded-lg bg-blue-600 text-white font-semibold hover:bg-blue-700">
                  Order Now
                </button>
                <button class="px-4 py-2 rounded-lg bg-white text-gray-900 font-semibold hover:bg-gray-200">
                  Learn More
                </button>
              </div>
            </div>
          </div>
        </swiper-slide>

        <!-- Slide 5 -->
        <swiper-slide>
          <div
            class="relative rounded-2xl overflow-hidden h-full flex items-end bg-cover bg-center"
            :style="{ backgroundImage: 'url(/src/components/public/cybertrack.jpg)' }"
          >
            <div class="bg-black/50 text-white p-4 sm:p-6 w-full">
              <h2 class="text-xl sm:text-2xl font-bold">Cybertrack</h2>
              <p class="text-xs sm:text-sm mt-2">Keep Your Adventure Alive, No Matter the Terrain</p>
              <div class="flex flex-wrap gap-3 mt-4">
                <button class="px-4 py-2 rounded-lg bg-blue-600 text-white font-semibold hover:bg-blue-700">
                  Order Now
                </button>
                <button class="px-4 py-2 rounded-lg bg-white text-gray-900 font-semibold hover:bg-gray-200">
                  Learn More
                </button>
              </div>
            </div>
          </div>
        </swiper-slide>
      </swiper>
    </div>

    <!-- Ready to Drive Sleek? Banner -->
    <div class="relative overflow-hidden bg-white mt-20 px-4 sm:px-10 lg:px-20 mb-10">
      <img
        src="/src/components/public/drive.jpg"
        alt="Blue EV car in motion"
        class="w-full h-64 sm:h-80 md:h-96 object-cover rounded-lg"
      />

      <div class="absolute inset-0 flex flex-col justify-center items-center sm:items-start px-6 sm:pl-16 md:pl-24 pb-6 sm:pb-12 text-white text-center sm:text-left">
        <h1 class="audiowide-regular text-2xl sm:text-3xl md:text-5xl font-bold leading-tight mb-4 sm:mb-6 tracking-wide">
          READY TO DRIVE<br />SLEEK?
        </h1>
      </div>
    </div>
  </section>
</template>

<style>
/* Swiper Pagination */
.swiper-pagination-bullet {
  @apply bg-gray-500 opacity-80;
}

.swiper-pagination-bullet-active {
  @apply bg-blue-600 scale-110;
}

/* Swiper Navigation */
.swiper-button-next,
.swiper-button-prev {
  @apply text-gray-600 hover:text-gray-800 transition-colors duration-300 !important;
}
</style>
