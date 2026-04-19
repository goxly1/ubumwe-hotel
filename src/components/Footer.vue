<template>
  <footer class="bg-slate-900 text-slate-300 py-16 border-t border-slate-800">
    <div class="container mx-auto px-6 md:px-12 grid grid-cols-1 md:grid-cols-4 gap-12">
      <!-- Brand -->
      <div class="col-span-1 md:col-span-1 flex flex-col gap-6">
        <div class="flex items-center gap-2">
          <div class="w-10 h-10 bg-brand-600 text-white rounded-lg flex items-center justify-center font-serif text-2xl font-bold">
            U
          </div>
          <span class="font-serif text-2xl font-bold text-white tracking-tight">UBUMWE</span>
        </div>
        <p class="text-sm leading-relaxed text-slate-400">
          Experience unparalleled luxury and breathtaking views at UBUMWE Hotel. Your perfect getaway in the heart of the city.
        </p>
      </div>

      <!-- Quick Links -->
      <div>
        <h4 class="text-white font-semibold mb-6">Quick Links</h4>
        <ul class="flex flex-col gap-4 text-sm mt-3">
          <li><router-link to="/" class="group flex items-center gap-2 hover:text-white transition-colors"><span class="w-3 h-[1px] bg-brand-500 transform scale-x-0 group-hover:scale-x-100 transition-transform origin-left"></span>Home</router-link></li>
          <li><router-link to="/about" class="group flex items-center gap-2 hover:text-white transition-colors"><span class="w-3 h-[1px] bg-brand-500 transform scale-x-0 group-hover:scale-x-100 transition-transform origin-left"></span>About Us</router-link></li>
          <li><router-link to="/contact" class="group flex items-center gap-2 hover:text-white transition-colors"><span class="w-3 h-[1px] bg-brand-500 transform scale-x-0 group-hover:scale-x-100 transition-transform origin-left"></span>Contact</router-link></li>
          <li><router-link to="/registration" class="group flex items-center gap-2 hover:text-white transition-colors"><span class="w-3 h-[1px] bg-brand-500 transform scale-x-0 group-hover:scale-x-100 transition-transform origin-left"></span>Registration</router-link></li>
        </ul>
      </div>

      <!-- Contact Info -->
      <div>
        <h4 class="text-white font-semibold mb-6">Contact Us</h4>
        <ul class="flex flex-col gap-4 text-sm">
          <li>
            <a href="mailto:info@ubumwehotel.com" class="flex items-center gap-3 hover:text-brand-400 transition-colors group">
              <div class="w-8 h-8 rounded-full bg-slate-800 flex items-center justify-center group-hover:bg-brand-600/20 group-hover:text-brand-400 transition-colors">
                <MailIcon class="w-4 h-4" />
              </div>
              info@ubumwehotel.com
            </a>
          </li>
          <li>
            <a href="tel:+250788123456" class="flex items-center gap-3 hover:text-brand-400 transition-colors group">
              <div class="w-8 h-8 rounded-full bg-slate-800 flex items-center justify-center group-hover:bg-brand-600/20 group-hover:text-brand-400 transition-colors">
                <PhoneIcon class="w-4 h-4" />
              </div>
              +250 788 123 456
            </a>
          </li>
          <li>
            <div class="flex items-start gap-3">
              <div class="w-8 h-8 rounded-full bg-slate-800 flex items-center justify-center shrink-0 mt-0.5">
                <MapPinIcon class="w-4 h-4" />
              </div>
              <span>KN 67 St, Kigali, Rwanda<br/>Downtown District</span>
            </div>
          </li>
        </ul>
      </div>

      <!-- Social -->
      <div>
        <h4 class="text-white font-semibold mb-6">Follow Us</h4>
        <div class="flex gap-4">
          <a href="https://facebook.com" target="_blank" rel="noopener noreferrer" class="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center hover:bg-[#1877F2] hover:text-white transition-all transform hover:-translate-y-1">
            <FacebookIcon class="w-5 h-5" />
          </a>
          <a href="https://twitter.com" target="_blank" rel="noopener noreferrer" class="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center hover:bg-[#1DA1F2] hover:text-white transition-all transform hover:-translate-y-1">
            <TwitterIcon class="w-5 h-5" />
          </a>
          <a href="https://instagram.com" target="_blank" rel="noopener noreferrer" class="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center hover:bg-gradient-to-tr hover:from-[#F56040] hover:to-[#C13584] hover:text-white transition-all transform hover:-translate-y-1">
            <InstagramIcon class="w-5 h-5" />
          </a>
          <a href="https://linkedin.com" target="_blank" rel="noopener noreferrer" class="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center hover:bg-[#0A66C2] hover:text-white transition-all transform hover:-translate-y-1">
            <LinkedinIcon class="w-5 h-5" />
          </a>
        </div>
      </div>
    </div>
    <div class="container mx-auto px-6 md:px-12 mt-16 pt-8 border-t border-slate-800 text-center text-sm text-slate-500">
      &copy; {{ new Date().getFullYear() }} UBUMWE Hotel. All rights reserved.
    </div>
  </footer>
</template>

<script setup>
import { Mail as MailIcon, Phone as PhoneIcon, MapPin as MapPinIcon, Facebook as FacebookIcon, Twitter as TwitterIcon, Instagram as InstagramIcon, Linkedin as LinkedinIcon } from 'lucide-vue-next'
</script>
