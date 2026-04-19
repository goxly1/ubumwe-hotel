<template>
  <div class="bg-slate-50 min-h-screen pb-24 pt-24">
    <!-- Header -->
    <div class="bg-brand-900 py-16 text-center mb-16 relative overflow-hidden">
      <div class="absolute inset-0 opacity-10">
        <img src="https://images.unsplash.com/photo-1542314831-c6a420b92312?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80" alt="Contact Background" class="w-full h-full object-cover">
      </div>
      <div class="relative z-10">
        <h1 class="text-4xl md:text-5xl font-serif text-white font-bold mb-4">Contact Us</h1>
        <p class="text-brand-100 max-w-2xl mx-auto">We're here to help make your stay exceptional. Reach out to us with any questions or requests.</p>
      </div>
    </div>

    <div class="container mx-auto px-6 md:px-12">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 max-w-6xl mx-auto">
        <!-- Contact Info -->
        <div>
          <h2 class="text-3xl font-serif font-bold text-slate-900 mb-8">Get in Touch</h2>
          
          <div class="space-y-8">
            <div class="flex items-start gap-4">
              <div class="w-12 h-12 rounded-full bg-brand-100 text-brand-600 flex items-center justify-center shrink-0">
                <MapPinIcon class="w-6 h-6" />
              </div>
              <div>
                <h3 class="text-lg font-bold text-slate-900 mb-1">Our Location</h3>
                <p class="text-slate-600 leading-relaxed">
                  KN 67 St, Kigali, Rwanda<br>
                  Downtown District, Kigali
                </p>
              </div>
            </div>

            <div class="flex items-start gap-4">
              <div class="w-12 h-12 rounded-full bg-brand-100 text-brand-600 flex items-center justify-center shrink-0">
                <PhoneIcon class="w-6 h-6" />
              </div>
              <div>
                <h3 class="text-lg font-bold text-slate-900 mb-1">Phone Number</h3>
                <p class="text-slate-600 leading-relaxed">
                  Front Desk: +250 788 123 456<br>
                  Reservations: +250 788 654 321
                </p>
              </div>
            </div>

            <div class="flex items-start gap-4">
              <div class="w-12 h-12 rounded-full bg-brand-100 text-brand-600 flex items-center justify-center shrink-0">
                <MailIcon class="w-6 h-6" />
              </div>
              <div>
                <h3 class="text-lg font-bold text-slate-900 mb-1">Email</h3>
                <p class="text-slate-600 leading-relaxed">
                  General: info@ubumwehotel.com<br>
                  Booking: reservations@ubumwehotel.com
                </p>
              </div>
            </div>
          </div>
        </div>

        <!-- Contact Form -->
        <div class="bg-white rounded-2xl shadow-xl p-8 md:p-10 border border-slate-100">
          <h3 class="text-2xl font-serif font-bold text-slate-900 mb-6">Send us a Message</h3>
          
          <form @submit.prevent="submitForm" class="space-y-6">
            <div v-if="successMsg" class="bg-green-50 text-green-700 p-4 rounded-lg flex items-center gap-3">
              <CheckCircleIcon class="w-5 h-5 text-green-500" />
              <span>{{ successMsg }}</span>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div>
                <label class="block text-sm font-medium text-slate-700 mb-2">First Name</label>
                <input v-model="form.firstName" type="text" required class="w-full px-4 py-3 rounded-lg border border-slate-200 focus:border-brand-500 focus:ring-2 focus:ring-brand-200 transition-all outline-none" placeholder="John">
              </div>
              <div>
                <label class="block text-sm font-medium text-slate-700 mb-2">Last Name</label>
                <input v-model="form.lastName" type="text" required class="w-full px-4 py-3 rounded-lg border border-slate-200 focus:border-brand-500 focus:ring-2 focus:ring-brand-200 transition-all outline-none" placeholder="Doe">
              </div>
            </div>

            <div>
              <label class="block text-sm font-medium text-slate-700 mb-2">Email Address</label>
              <input v-model="form.email" type="email" required class="w-full px-4 py-3 rounded-lg border border-slate-200 focus:border-brand-500 focus:ring-2 focus:ring-brand-200 transition-all outline-none" placeholder="john@example.com">
            </div>

            <div>
              <label class="block text-sm font-medium text-slate-700 mb-2">Message</label>
              <textarea v-model="form.message" required rows="4" class="w-full px-4 py-3 rounded-lg border border-slate-200 focus:border-brand-500 focus:ring-2 focus:ring-brand-200 transition-all outline-none resize-none" placeholder="How can we help you?"></textarea>
            </div>

            <button type="submit" class="w-full bg-brand-600 hover:bg-brand-700 text-white font-medium py-3.5 rounded-lg transition-all shadow-md hover:shadow-lg flex items-center justify-center gap-2">
              <SendIcon class="w-4 h-4" />
              Send Message
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
import { MapPin as MapPinIcon, Phone as PhoneIcon, Mail as MailIcon, CheckCircle as CheckCircleIcon, Send as SendIcon } from 'lucide-vue-next'

const form = reactive({
  firstName: '',
  lastName: '',
  email: '',
  message: ''
})

const successMsg = ref('')

const submitForm = () => {
  // Simulate API call
  setTimeout(() => {
    successMsg.value = 'Thank you! Your message has been received. We will get back to you shortly.'
    form.firstName = ''
    form.lastName = ''
    form.email = ''
    form.message = ''
    
    setTimeout(() => {
      successMsg.value = ''
    }, 5000)
  }, 800)
}
</script>
