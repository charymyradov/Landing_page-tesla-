<template>
    <nav class="w-full z-50 text-right fixed transition-transform duration-300 ease-in-out"
        :class="[
            inHero ? 'bg-transparent' : (showNavbar ? 'bg-black/95 shadow-lg' : 'bg-black/95'),
            showNavbar ? 'translate-y-0' : '-translate-y-full'
        ]">
        <div class="flex justify-between items-center py-6 border-b transition-colors duration-300"
            :class="inHero ? 'border-white/20' : 'border-gray-800'">
            <!-- Logo -->
            <div class="absolute left-6 md:left-20">
                <img src="/tesla-motors.svg" alt="Tesla Logo" class="w-36 md:w-44" />
            </div>

            <div class="hidden md:flex w-full justify-end space-x-8">
                <a href="#home" class="text-white hover:text-gray-400 transition audiowide-regular focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-offset-2 focus-visible:ring-offset-transparent rounded px-2 py-1">Home</a>
                <a href="#models" class="text-white hover:text-gray-400 transition audiowide-regular focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-offset-2 focus-visible:ring-offset-transparent rounded px-2 py-1">Models</a>
                <a href="#charging" class="text-white hover:text-gray-400 transition audiowide-regular focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-offset-2 focus-visible:ring-offset-transparent rounded px-2 py-1">Charging</a>
                <a href="#discover" class="text-white hover:text-gray-400 transition audiowide-regular focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-offset-2 focus-visible:ring-offset-transparent rounded px-2 py-1">Discover</a>
            </div>

            <div class="md:hidden flex items-center">
                <button @click.stop="toggleMobileMenu" class="text-white focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-white rounded p-1" :aria-label="mobileMenuOpen ? 'Menüyü kapat' : 'Menüyü aç'" :aria-expanded="mobileMenuOpen">
                    <svg v-if="!mobileMenuOpen" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
                    </svg>
                    <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>
            </div>
        </div>

        <!-- Mobile Menu -->
        <transition
            enter-active-class="transition duration-300 ease-out"
            enter-from-class="opacity-0 -translate-y-4"
            enter-to-class="opacity-100 translate-y-0"
            leave-active-class="transition duration-200 ease-in"
            leave-from-class="opacity-100 translate-y-0"
            leave-to-class="opacity-0 -translate-y-4"
        >
            <div v-if="mobileMenuOpen"
                class="md:hidden bg-black/95 text-right px-6 py-8 absolute w-full z-40">
                <div class="space-y-6">
                    <a href="#home" @click="handleLinkClick('#home')"
                        class="block text-white text-2xl hover:text-gray-400 transition audiowide-regular focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-white rounded px-2 py-1">Home</a>
                    <a href="#models" @click="handleLinkClick('#models')"
                        class="block text-white text-2xl hover:text-gray-400 transition audiowide-regular focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-white rounded px-2 py-1">Models</a>
                    <a href="#charging" @click="handleLinkClick('#charging')"
                        class="block text-white text-2xl hover:text-gray-400 transition audiowide-regular focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-white rounded px-2 py-1">Charging</a>
                    <a href="#discover" @click="handleLinkClick('#discover')"
                        class="block text-white text-2xl hover:text-gray-400 transition audiowide-regular focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-white rounded px-2 py-1">Discover</a>
                </div>
            </div>
        </transition>
    </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const mobileMenuOpen = ref(false);
const showNavbar = ref(true);
const inHero = ref(true);

let lastScrollY = 0;
const SCROLL_THRESHOLD = 10;

function toggleMobileMenu() {
    mobileMenuOpen.value = !mobileMenuOpen.value;
}

function scrollToSection(targetId) {
    const element = document.getElementById(targetId.replace('#', ''));
    if (element) {
        element.scrollIntoView({ behavior: 'smooth', block: 'start' });
    }
}

function handleLinkClick(targetId) {
    mobileMenuOpen.value = false;
    scrollToSection(targetId);
}

function handleScroll() {
    const currentScrollY = window.scrollY;
    const viewportHeight = window.innerHeight;

    // Hero section içinde mi?
    inHero.value = currentScrollY < viewportHeight;

    // Hero section içindeyse her zaman göster
    if (inHero.value) {
        showNavbar.value = true;
        lastScrollY = currentScrollY;
        return;
    }

    // Eşik kadar hareket yoksa hair tagme
    if (Math.abs(currentScrollY - lastScrollY) < SCROLL_THRESHOLD) {
        return;
    }

    // Aşağı kaydır → gizle, yukarı kaydır → göster
    if (currentScrollY > lastScrollY) {
        showNavbar.value = false;
    } else {
        showNavbar.value = true;
    }

    lastScrollY = currentScrollY;
}

function handleDocumentClick() {
    if (mobileMenuOpen.value) {
        mobileMenuOpen.value = false;
    }
}

function handleAnchorClick(e) {
    e.preventDefault();
    const targetId = e.currentTarget.getAttribute('href');
    handleLinkClick(targetId);
}

onMounted(() => {
    window.addEventListener('scroll', handleScroll, { passive: true });
    document.addEventListener('click', handleDocumentClick);
    document.querySelectorAll('a[href^="#"]').forEach((anchor) => {
        anchor.addEventListener('click', handleAnchorClick);
    });
});

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll);
    document.removeEventListener('click', handleDocumentClick);
});
</script>
