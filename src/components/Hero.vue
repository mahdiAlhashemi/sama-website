<script setup>
const props = defineProps({
  content: Object,
  isRtl: Boolean
})
</script>

<template>
  <section id="home" class="relative min-h-screen flex items-center gradient-hero overflow-hidden">
    <!-- Animated Background Elements -->
    <div class="absolute inset-0 overflow-hidden">
      <div class="absolute top-20 left-10 w-72 h-72 bg-blue-500/20 rounded-full blur-3xl animate-float"></div>
      <div class="absolute bottom-20 right-10 w-96 h-96 bg-cyan-500/20 rounded-full blur-3xl animate-float" style="animation-delay: 1s;"></div>
      <div class="absolute top-1/2 left-1/2 w-64 h-64 bg-indigo-500/10 rounded-full blur-3xl animate-float" style="animation-delay: 2s;"></div>

      <!-- Grid Pattern -->
      <div class="absolute inset-0 opacity-5">
        <div class="h-full w-full" style="background-image: linear-gradient(rgba(255,255,255,.1) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,.1) 1px, transparent 1px); background-size: 50px 50px;"></div>
      </div>
    </div>

    <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pt-24">
      <div class="grid lg:grid-cols-2 gap-12 items-center">
        <!-- Content -->
        <div class="text-white animate-fade-in">
          <div class="inline-flex items-center gap-2 bg-white/10 backdrop-blur-sm px-4 py-2 rounded-full mb-6">
            <span class="w-2 h-2 bg-green-400 rounded-full animate-pulse"></span>
            <span class="text-sm font-medium">{{ isRtl ? 'شريك Odoo الرسمي' : 'Official Odoo Partner' }}</span>
          </div>

          <h1 class="text-4xl md:text-5xl lg:text-6xl font-bold mb-4 leading-tight">
            {{ content.title }}
          </h1>

          <h2 class="text-xl md:text-2xl font-semibold text-blue-300 mb-4">
            {{ content.subtitle }}
          </h2>

          <p class="text-lg text-blue-200 mb-4 font-medium">
            {{ content.slogan }}
          </p>

          <p class="text-white/80 mb-8 text-lg leading-relaxed max-w-xl">
            {{ content.welcome }}
          </p>

          <div class="flex flex-wrap gap-4">
            <a href="#services" class="btn-primary bg-white text-[#1e3a5f] hover:bg-blue-50">
              <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z" />
              </svg>
              {{ content.cta1 }}
            </a>
            <a href="#contact" class="btn-secondary border-white text-white hover:bg-white hover:text-[#1e3a5f]">
              {{ content.cta2 }}
            </a>
          </div>

          <!-- Trust Badges -->
          <div class="mt-12 flex items-center gap-8">
            <div class="text-center">
              <div class="text-3xl font-bold text-white">+12</div>
              <div class="text-sm text-blue-200">{{ isRtl ? 'سنة خبرة' : 'Years' }}</div>
            </div>
            <div class="w-px h-12 bg-white/20"></div>
            <div class="text-center">
              <div class="text-3xl font-bold text-white">+500</div>
              <div class="text-sm text-blue-200">{{ isRtl ? 'مشروع' : 'Projects' }}</div>
            </div>
            <div class="w-px h-12 bg-white/20"></div>
            <div class="text-center">
              <div class="text-3xl font-bold text-white">Odoo</div>
              <div class="text-sm text-blue-200">{{ isRtl ? 'شريك رسمي' : 'Partner' }}</div>
            </div>
          </div>
        </div>

        <!-- Hero Image/Illustration -->
        <div class="hidden lg:block animate-float">
          <div class="relative">
            <div class="absolute inset-0 bg-gradient-to-r from-blue-500 to-cyan-500 rounded-3xl blur-2xl opacity-30"></div>
            <div class="relative bg-white/10 backdrop-blur-md rounded-3xl p-8 border border-white/20">
              <!-- Dashboard Preview -->
              <div class="bg-white rounded-2xl p-6 shadow-2xl">
                <div class="flex items-center gap-2 mb-4">
                  <div class="w-3 h-3 rounded-full bg-red-500"></div>
                  <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
                  <div class="w-3 h-3 rounded-full bg-green-500"></div>
                </div>
                <div class="space-y-3">
                  <div class="h-4 bg-gray-100 rounded w-3/4"></div>
                  <div class="h-4 bg-gray-100 rounded w-1/2"></div>
                  <div class="grid grid-cols-3 gap-3 mt-4">
                    <div class="h-20 bg-blue-100 rounded-lg"></div>
                    <div class="h-20 bg-green-100 rounded-lg"></div>
                    <div class="h-20 bg-purple-100 rounded-lg"></div>
                  </div>
                  <div class="h-32 bg-gradient-to-r from-blue-500 to-cyan-500 rounded-lg mt-4 opacity-80"></div>
                </div>
              </div>

              <!-- Floating Elements -->
              <div class="absolute -top-4 -right-4 bg-white rounded-xl p-3 shadow-lg animate-float" style="animation-delay: 0.5s;">
                <div class="flex items-center gap-2">
                  <div class="w-8 h-8 bg-green-100 rounded-full flex items-center justify-center">
                    <svg class="w-4 h-4 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                    </svg>
                  </div>
                  <span class="text-sm font-medium text-gray-700">ERP Active</span>
                </div>
              </div>

              <div class="absolute -bottom-4 -left-4 bg-white rounded-xl p-3 shadow-lg animate-float" style="animation-delay: 1s;">
                <div class="flex items-center gap-2">
                  <div class="w-8 h-8 bg-blue-100 rounded-full flex items-center justify-center">
                    <svg class="w-4 h-4 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6" />
                    </svg>
                  </div>
                  <span class="text-sm font-medium text-gray-700">+95%</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll Indicator -->
    <div class="absolute bottom-8 left-1/2 -translate-x-1/2 animate-bounce">
      <a href="#about" class="flex flex-col items-center text-white/60 hover:text-white transition-colors">
        <span class="text-sm mb-2">{{ isRtl ? 'اكتشف المزيد' : 'Discover More' }}</span>
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
        </svg>
      </a>
    </div>
  </section>
</template>
