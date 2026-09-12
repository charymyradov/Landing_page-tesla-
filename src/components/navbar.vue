<template>
    <nav class="bg-black w-full opacity-45 z-50 text-right fixed" @click.stop="handleNavClick">
        <div class="flex justify-between items-center py-6 border-b border-gray-800 px-6 md:px-20">
            <!-- Logo -->
            <div class="absolute left-6 md:left-20">
                <img src="/tesla-motors.svg" alt="Tesla Logo" class="w-36 md:w-44" />
            </div>


            <div class="hidden md:flex w-full justify-end space-x-8">
                <a href="#home" class="text-white hover:text-gray-400 transition audiowide-regular">Home</a>
                <a href="#models" class="text-white hover:text-gray-400 transition audiowide-regular">Models</a>
                <a href="#charging" class="text-white hover:text-gray-400 transition audiowide-regular">Charging</a>
                <a href="#discover" class="text-white hover:text-gray-400 transition audiowide-regular">Discover</a>
            </div>

            <div class="md:hidden flex items-center">
                <button @click.stop="toggleMobileMenu" class="text-white focus:outline-none" aria-label="Toggle menu">
                    <i class="fas" :class="mobileMenuOpen ? 'fa-times' : 'fa-bars'" />
                </button>
            </div>
        </div>


        <div v-show="mobileMenuOpen"
            class="md:hidden bg-black bg-opacity-95 text-right px-6 py-8 absolute w-full z-40 transition-all duration-300 ease-in-out"
            :class="{ 'opacity-100 transform translate-y-0': mobileMenuOpen, 'opacity-0 transform -translate-y-2 pointer-events-none': !mobileMenuOpen }">
            <div class="space-y-6">
                <a href="#home" @click="handleLinkClick('#home')"
                    class="block text-white text-2xl hover:text-gray-400 transition audiowide-regular">Home</a>
                <a href="#models" @click="handleLinkClick('#models')"
                    class="block text-white text-2xl hover:text-gray-400 transition audiowide-regular">Models</a>
                <a href="#charging" @click="handleLinkClick('#charging')"
                    class="block text-white text-2xl hover:text-gray-400 transition audiowide-regular">Charging</a>
                <a href="#discover" @click="handleLinkClick('#discover')"
                    class="block text-white text-2xl hover:text-gray-400 transition audiowide-regular">Discover</a>
            </div>
        </div>
    </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const mobileMenuOpen = ref(false);

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
    document.addEventListener('click', handleDocumentClick);
    document.querySelectorAll('a[href^="#"]').forEach((anchor) => {
        anchor.addEventListener('click', handleAnchorClick);
    });
});

onUnmounted(() => {
    document.removeEventListener('click', handleDocumentClick);
});
</script>

<style scoped>
.fas {
    font-size: 1.5rem;
}
</style>