<template>
  <div>
    <!-- Hero Section -->
    <section class="relative h-screen flex items-center justify-center overflow-hidden">
      <div class="absolute inset-0 z-0 overflow-hidden">
        <img src="https://images.unsplash.com/photo-1566073771259-6a8506099945?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80" alt="UBUMWE Hotel Exterior" class="w-full h-full object-cover animate-[kenburns_20s_ease-in-out_infinite_alternate]" />
        <div class="absolute inset-0 bg-slate-900/40 bg-gradient-to-t from-slate-900/80 via-transparent to-transparent"></div>
      </div>
      
      <div class="relative z-10 text-center px-6 max-w-4xl mx-auto mt-16">
        <span class="text-brand-300 font-medium tracking-wider uppercase mb-4 block">Welcome to Your Sanctuary</span>
        <h1 class="text-5xl md:text-7xl font-serif text-white font-bold mb-6 leading-tight">
          Discover True <br/> <span class="text-transparent bg-clip-text bg-gradient-to-r from-brand-300 to-white">Rwandan Elegance</span>
        </h1>
        <p class="text-lg md:text-xl text-slate-200 mb-10 max-w-2xl mx-auto leading-relaxed">
          Situated in the vibrant heart of the city, UBUMWE Hotel offers breathtaking views, exceptional comfort, and a rich cultural experience.
        </p>
        <div class="flex flex-col sm:flex-row gap-5 justify-center">
          <router-link to="/registration" class="relative group overflow-hidden bg-brand-600 text-white px-8 py-4 rounded-full font-semibold transition-all transform hover:-translate-y-1 shadow-xl shadow-brand-600/30">
            <span class="relative z-10 transition-colors group-hover:text-white">Book Your Stay</span>
            <div class="absolute inset-0 bg-gradient-to-r from-brand-500 to-brand-700 opacity-0 group-hover:opacity-100 transition-opacity duration-300 rounded-full z-0"></div>
          </router-link>
          <router-link to="/about" class="relative overflow-hidden group bg-white/10 hover:bg-white/20 backdrop-blur-md text-white border border-white/30 px-8 py-4 rounded-full font-semibold transition-all transform hover:-translate-y-1">
            <span class="relative z-10">Explore Hotel</span>
            <div class="absolute inset-0 bg-white/5 opacity-0 group-hover:opacity-100 transition-opacity duration-300 rounded-full z-0"></div>
          </router-link>
        </div>
      </div>
    </section>

    <!-- Features Section -->
    <section class="py-24 bg-white relative">
      <div class="container mx-auto px-6 md:px-12">
        <div class="text-center max-w-2xl mx-auto mb-16">
          <h2 class="text-4xl font-serif font-bold text-slate-900 mb-4">World-Class Amenities</h2>
          <p class="text-slate-600">Everything you need for an unforgettable stay, carefully curated for your maximum comfort and enjoyment.</p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-12">
          <div class="group cursor-pointer">
            <div class="overflow-hidden rounded-2xl mb-6 shadow-xl aspect-[4/3]">
              <img src="https://images.unsplash.com/photo-1582719478250-c89cae4dc85b?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Luxury Rooms" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700" />
            </div>
            <h3 class="text-2xl font-serif font-bold text-slate-900 mb-2">Luxury Suites</h3>
            <p class="text-slate-600 leading-relaxed">Spacious, elegantly designed rooms offering panoramic city views and premium bedding.</p>
          </div>
          
          <div class="group cursor-pointer mt-0 md:mt-12">
            <div class="overflow-hidden rounded-2xl mb-6 shadow-xl aspect-[4/3]">
              <img src="https://images.unsplash.com/photo-1544148103-0773bf10d330?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Infinity Pool" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700" />
            </div>
            <h3 class="text-2xl font-serif font-bold text-slate-900 mb-2">Rooftop Infinity Pool</h3>
            <p class="text-slate-600 leading-relaxed">Relax in our iconic rooftop pool while taking in the stunning skyline views.</p>
          </div>
          
          <div class="group cursor-pointer">
            <div class="overflow-hidden rounded-2xl mb-6 shadow-xl aspect-[4/3]">
              <img src="https://images.unsplash.com/photo-1514933651103-005eec06c04b?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Fine Dining" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700" />
            </div>
            <h3 class="text-2xl font-serif font-bold text-slate-900 mb-2">Fine Dining</h3>
            <p class="text-slate-600 leading-relaxed">Savor exquisite international and local cuisine prepared by award-winning chefs.</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
@keyframes kenburns {
  0% { transform: scale(1); }
  100% { transform: scale(1.05); }
}
</style>
