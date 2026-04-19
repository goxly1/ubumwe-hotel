<template>
  <div class="bg-slate-50 min-h-screen py-24">
    <div class="container mx-auto px-6 md:px-12">
      
      <div class="max-w-3xl mx-auto mb-12 text-center">
        <h1 class="text-4xl md:text-5xl font-serif font-bold text-slate-900 mb-4">Book Your Stay</h1>
        <p class="text-lg text-slate-600">Reserve your luxury experience at UBUMWE Hotel today.</p>
      </div>

      <div class="max-w-3xl mx-auto bg-white rounded-2xl shadow-xl overflow-hidden border border-slate-100 relative">
        <!-- Success State -->
        <div v-if="isSuccess" class="absolute inset-0 bg-white z-20 flex flex-col items-center justify-center p-8 text-center animate-fade-in">
          <div class="w-20 h-20 bg-green-100 text-green-500 rounded-full flex items-center justify-center mb-6">
            <CheckIcon class="w-10 h-10" />
          </div>
          <h2 class="text-3xl font-serif font-bold text-slate-900 mb-4">Reservation Confirmed!</h2>
          <p class="text-slate-600 max-w-md mx-auto mb-8">
            Thank you, <span class="font-semibold">{{ form.firstName }}</span>. Your booking for a <span class="font-semibold">{{ getRoomName(form.roomType) }}</span> has been received. We have sent the details to {{ form.email }}.
          </p>
          <button @click="resetForm" class="bg-brand-600 hover:bg-brand-700 text-white px-8 py-3 rounded-full font-medium transition-all">
            Make Another Booking
          </button>
        </div>

        <div class="p-8 md:p-12">
          <form @submit.prevent="submitForm">
            <!-- Personal Info -->
            <div class="mb-8">
              <h3 class="text-xl font-serif font-semibold text-slate-900 mb-6 pb-2 border-b border-slate-100">Personal Information</h3>
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                  <label class="block text-sm font-medium text-slate-700 mb-2">First Name *</label>
                  <input v-model="form.firstName" type="text" required class="form-input" placeholder="Enter your first name">
                  <p v-if="errors.firstName" class="text-red-500 text-xs mt-1">{{ errors.firstName }}</p>
                </div>
                <div>
                  <label class="block text-sm font-medium text-slate-700 mb-2">Last Name *</label>
                  <input v-model="form.lastName" type="text" required class="form-input" placeholder="Enter your last name">
                  <p v-if="errors.lastName" class="text-red-500 text-xs mt-1">{{ errors.lastName }}</p>
                </div>
                <div>
                  <label class="block text-sm font-medium text-slate-700 mb-2">Email Address *</label>
                  <input v-model="form.email" type="email" required class="form-input" placeholder="Enter your email">
                  <p v-if="errors.email" class="text-red-500 text-xs mt-1">{{ errors.email }}</p>
                </div>
                <div>
                  <label class="block text-sm font-medium text-slate-700 mb-2">Phone Number *</label>
                  <input v-model="form.phone" type="tel" required class="form-input" placeholder="+250 XXX XXX XXX">
                  <p v-if="errors.phone" class="text-red-500 text-xs mt-1">{{ errors.phone }}</p>
                </div>
              </div>
            </div>

            <!-- Booking Details -->
            <div class="mb-8">
              <h3 class="text-xl font-serif font-semibold text-slate-900 mb-6 pb-2 border-b border-slate-100">Booking Details</h3>
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="md:col-span-2">
                  <label class="block text-sm font-medium text-slate-700 mb-2">Room Type *</label>
                  <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                    <label class="relative cursor-pointer">
                      <input type="radio" v-model="form.roomType" value="standard" class="peer sr-only" name="roomType">
                      <div class="p-4 rounded-xl border-2 border-slate-200 peer-checked:border-brand-500 peer-checked:bg-brand-50 transition-all text-center hover:border-brand-300">
                        <div class="font-semibold text-slate-900 mb-1">Standard Room</div>
                        <div class="text-sm text-slate-500">$150 / night</div>
                      </div>
                    </label>
                    <label class="relative cursor-pointer">
                      <input type="radio" v-model="form.roomType" value="deluxe" class="peer sr-only" name="roomType">
                      <div class="p-4 rounded-xl border-2 border-slate-200 peer-checked:border-brand-500 peer-checked:bg-brand-50 transition-all text-center hover:border-brand-300">
                        <div class="font-semibold text-slate-900 mb-1">Deluxe Suite</div>
                        <div class="text-sm text-slate-500">$250 / night</div>
                      </div>
                    </label>
                    <label class="relative cursor-pointer">
                      <input type="radio" v-model="form.roomType" value="presidential" class="peer sr-only" name="roomType">
                      <div class="p-4 rounded-xl border-2 border-slate-200 peer-checked:border-brand-500 peer-checked:bg-brand-50 transition-all text-center hover:border-brand-300">
                        <div class="font-semibold text-slate-900 mb-1">Presidential</div>
                        <div class="text-sm text-slate-500">$500 / night</div>
                      </div>
                    </label>
                  </div>
                  <p v-if="errors.roomType" class="text-red-500 text-xs mt-2">{{ errors.roomType }}</p>
                </div>
                
                <div>
                  <label class="block text-sm font-medium text-slate-700 mb-2">Check-in Date *</label>
                  <input v-model="form.checkIn" type="date" required class="form-input">
                  <p v-if="errors.checkIn" class="text-red-500 text-xs mt-1">{{ errors.checkIn }}</p>
                </div>
                <div>
                  <label class="block text-sm font-medium text-slate-700 mb-2">Check-out Date *</label>
                  <input v-model="form.checkOut" type="date" required class="form-input">
                  <p v-if="errors.checkOut" class="text-red-500 text-xs mt-1">{{ errors.checkOut }}</p>
                </div>
                
                <div>
                  <label class="block text-sm font-medium text-slate-700 mb-2">Guests *</label>
                  <select v-model="form.guests" required class="form-input">
                    <option value="" disabled>Select guests</option>
                    <option value="1">1 Adult</option>
                    <option value="2">2 Adults</option>
                    <option value="3">3 Adults</option>
                    <option value="4">4 Adults</option>
                  </select>
                  <p v-if="errors.guests" class="text-red-500 text-xs mt-1">{{ errors.guests }}</p>
                </div>
              </div>
            </div>

            <!-- Special Requests -->
            <div class="mb-8">
              <label class="block text-sm font-medium text-slate-700 mb-2">Special Requests (Optional)</label>
              <textarea v-model="form.requests" rows="3" class="form-input resize-none" placeholder="Any special requirements or requests?"></textarea>
            </div>

            <button type="submit" :disabled="isSubmitting" class="w-full bg-slate-900 hover:bg-slate-800 text-white font-medium py-4 rounded-xl transition-all shadow-xl shadow-slate-900/20 text-lg flex justify-center items-center gap-2 disabled:opacity-70">
              <span v-if="!isSubmitting">Complete Reservation</span>
              <Loader2Icon v-else class="w-6 h-6 animate-spin" />
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
import { Check as CheckIcon, Loader2 as Loader2Icon } from 'lucide-vue-next'

const formDefault = {
  firstName: '',
  lastName: '',
  email: '',
  phone: '',
  roomType: '',
  checkIn: '',
  checkOut: '',
  guests: '',
  requests: ''
}

const form = reactive({ ...formDefault })
const errors = reactive({})
const isSubmitting = ref(false)
const isSuccess = ref(false)

const validateEmail = (email) => {
  return String(email)
    .toLowerCase()
    .match(
      /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|.(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
    );
};

const validateForm = () => {
  let isValid = true
  Object.keys(errors).forEach(key => errors[key] = '')

  if (!form.firstName.trim()) { errors.firstName = 'First name is required'; isValid = false }
  if (!form.lastName.trim()) { errors.lastName = 'Last name is required'; isValid = false }
  
  if (!form.email.trim()) { 
    errors.email = 'Email is required'; isValid = false 
  } else if (!validateEmail(form.email)) {
    errors.email = 'Please enter a valid email'; isValid = false
  }
  
  if (!form.phone.trim()) { errors.phone = 'Phone number is required'; isValid = false }
  if (!form.roomType) { errors.roomType = 'Please select a room type'; isValid = false }
  if (!form.checkIn) { errors.checkIn = 'Check-in date is required'; isValid = false }
  if (!form.checkOut) { errors.checkOut = 'Check-out date is required'; isValid = false }
  if (!form.guests) { errors.guests = 'Please select number of guests'; isValid = false }

  // Check valid dates
  if (form.checkIn && form.checkOut) {
    if (new Date(form.checkIn) >= new Date(form.checkOut)) {
      errors.checkOut = 'Check-out date must be after check-in date'
      isValid = false
    }
  }

  return isValid
}

const submitForm = () => {
  if (validateForm()) {
    isSubmitting.value = true
    
    // Simulate API call
    setTimeout(() => {
      isSubmitting.value = false
      isSuccess.value = true
    }, 1500)
  }
}

const getRoomName = (value) => {
  const map = {
    standard: 'Standard Room',
    deluxe: 'Deluxe Suite',
    presidential: 'Presidential Suite'
  }
  return map[value] || value
}

const resetForm = () => {
  Object.assign(form, formDefault)
  isSuccess.value = false
}
</script>

<style scoped>
.form-input {
  @apply w-full px-4 py-3 rounded-xl border border-slate-200 focus:border-brand-500 focus:ring-2 focus:ring-brand-200 transition-all outline-none bg-slate-50 focus:bg-white;
}

.animate-fade-in {
  animation: fadeIn 0.5s ease-out forwards;
}

@keyframes fadeIn {
  from { opacity: 0; transform: scale(0.95); }
  to { opacity: 1; transform: scale(1); }
}
</style>
