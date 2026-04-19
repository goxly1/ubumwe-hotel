<template>
  <header class="fixed top-0 w-full z-50 transition-all duration-500" :class="[isScrolled ? 'bg-white/80 backdrop-blur-xl shadow-lg border-b border-white/20 py-3' : 'bg-transparent py-6', $route.path !== '/' ? 'bg-white/90 backdrop-blur-xl shadow-sm border-b border-slate-100' : '']">
    <div class="container mx-auto px-6 md:px-12 flex justify-between items-center">
      <router-link to="/" class="group flex items-center gap-2">
        <div class="w-10 h-10 bg-brand-600 text-white rounded-lg flex items-center justify-center font-serif text-2xl font-bold group-hover:bg-brand-700 transition-colors">
          U
        </div>
        <span class="font-serif text-2xl font-bold tracking-tight" :class="[$route.path === '/' && !isScrolled ? 'text-white' : 'text-slate-900']">
          UBUMWE
        </span>
      </router-link>

      <!-- Desktop Menu -->
      <nav class="hidden md:flex items-center gap-10">
        <router-link 
          v-for="link in links" 
          :key="link.path" 
          :to="link.path"
          class="text-sm font-semibold tracking-wide transition-all relative py-2 group/navlink"
          :class="[$route.path === '/' && !isScrolled ? 'text-white/90 hover:text-white' : 'text-slate-600 hover:text-brand-600']"
        >
          {{ link.name }}
          <span 
            class="absolute -bottom-1 left-0 w-full h-0.5 transform origin-left transition-transform duration-300 ease-out"
            :class="[$route.path === link.path ? 'scale-x-100 bg-brand-500' : 'scale-x-0 group-hover/navlink:scale-x-100 bg-current']"
          ></span>
        </router-link>
        <router-link to="/registration" class="relative overflow-hidden bg-brand-600 group text-white px-7 py-2.5 rounded-full text-sm font-semibold transition-all shadow-lg hover:shadow-brand-500/50 transform hover:-translate-y-1">
          <span class="relative z-10 transition-colors group-hover:text-white">Book Now</span>
          <div class="absolute inset-0 bg-gradient-to-r from-brand-500 to-brand-700 opacity-0 group-hover:opacity-100 transition-opacity duration-300 rounded-full z-0"></div>
        </router-link>
      </nav>

      <!-- Mobile Menu Button -->
      <button @click="isOpen = !isOpen" class="md:hidden text-2xl z-50 relative" :class="[$route.path === '/' && !isScrolled && !isOpen ? 'text-white' : 'text-slate-900']">
        <MenuIcon v-if="!isOpen" />
        <XIcon v-else />
      </button>
    </div>

    <!-- Mobile Menu -->
    <transition name="slide">
      <div v-if="isOpen" class="fixed inset-0 bg-white z-40 md:hidden pt-24 px-6 flex flex-col items-center gap-8 h-screen w-full">
        <router-link 
          v-for="link in links" 
          :key="link.path" 
          :to="link.path"
          class="text-2xl font-serif text-slate-800"
          @click="isOpen = false"
        >
          {{ link.name }}
        </router-link>
        <router-link 
          to="/registration" 
          class="bg-brand-600 text-white px-8 py-3 rounded-full text-lg font-medium mt-4 w-full text-center"
          @click="isOpen = false"
        >
          Book Now
        </router-link>
      </div>
    </transition>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { Menu as MenuIcon, X as XIcon } from 'lucide-vue-next'

const links = [
  { name: 'Home', path: '/' },
  { name: 'About', path: '/about' },
  { name: 'Contact', path: '/contact' }
]

const isScrolled = ref(false)
const isOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.slide-enter-active,
.slide-leave-active {
  transition: transform 0.4s ease-in-out;
}

.slide-enter-from,
.slide-leave-to {
  transform: translateY(-100%);
}
</style>
