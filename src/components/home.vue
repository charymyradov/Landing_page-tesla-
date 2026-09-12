<template>
    <section id="home" class="relative w-full overflow-hidden">
      
        <div class="absolute inset-0 w-full h-full">
            <video autoplay loop muted playsinline preload="auto" class="w-full h-full object-cover">
                <source src="/wideo.mp4" type="video/mp4" />
                
            </video>
        </div>

        
        <div class="absolute inset-0 bg-black/30"></div>

        
       
    </section>
</template>

<style scoped>

section {
    min-height: 100vh;
}


video {
    transform: translateZ(0);
    backface-visibility: hidden;
}
</style>