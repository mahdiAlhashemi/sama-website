<script setup>
const props = defineProps({
  content: Object,
  isRtl: Boolean
})
</script>

<template>
  <section id="about" class="py-24 bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <span class="inline-block px-4 py-2 bg-blue-100 text-blue-700 rounded-full text-sm font-semibold mb-4">
          {{ isRtl ? 'تعرف علينا' : 'Get to Know Us' }}
        </span>
        <h2 class="section-title text-gray-900">{{ content.title }}</h2>
      </div>

      <div class="grid lg:grid-cols-2 gap-16 items-center">
        <!-- Image Side -->
        <div class="relative">
          <div class="relative z-10">
            <div class="bg-gradient-to-br from-[#1e3a5f] to-[#2980b9] rounded-3xl p-1">
              <div class="bg-white rounded-3xl p-8">
                <div class="grid grid-cols-2 gap-4">
                  <div class="bg-blue-50 rounded-2xl p-6 text-center">
                    <div class="text-4xl font-bold text-[#1e3a5f]">2012</div>
                    <div class="text-gray-600 mt-2">{{ isRtl ? 'سنة التأسيس' : 'Founded' }}</div>
                  </div>
                  <div class="bg-green-50 rounded-2xl p-6 text-center">
                    <div class="text-4xl font-bold text-green-600">+500</div>
                    <div class="text-gray-600 mt-2">{{ isRtl ? 'مشروع' : 'Projects' }}</div>
                  </div>
                  <div class="bg-purple-50 rounded-2xl p-6 text-center">
                    <div class="text-4xl font-bold text-purple-600">Odoo</div>
                    <div class="text-gray-600 mt-2">{{ isRtl ? 'شريك رسمي' : 'Partner' }}</div>
                  </div>
                  <div class="bg-orange-50 rounded-2xl p-6 text-center">
                    <div class="text-4xl font-bold text-orange-600">+200</div>
                    <div class="text-gray-600 mt-2">{{ isRtl ? 'عميل' : 'Clients' }}</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!-- Decorative Elements -->
          <div class="absolute -top-4 -right-4 w-24 h-24 bg-blue-200 rounded-full opacity-50 blur-xl"></div>
          <div class="absolute -bottom-4 -left-4 w-32 h-32 bg-cyan-200 rounded-full opacity-50 blur-xl"></div>
        </div>

        <!-- Content Side -->
        <div>
          <div class="inline-flex items-center gap-2 bg-green-100 text-green-700 px-4 py-2 rounded-full text-sm font-semibold mb-6">
            <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 20 20">
              <path fill-rule="evenodd" d="M6.267 3.455a3.066 3.066 0 001.745-.723 3.066 3.066 0 013.976 0 3.066 3.066 0 001.745.723 3.066 3.066 0 012.812 2.812c.051.643.304 1.254.723 1.745a3.066 3.066 0 010 3.976 3.066 3.066 0 00-.723 1.745 3.066 3.066 0 01-2.812 2.812 3.066 3.066 0 00-1.745.723 3.066 3.066 0 01-3.976 0 3.066 3.066 0 00-1.745-.723 3.066 3.066 0 01-2.812-2.812 3.066 3.066 0 00-.723-1.745 3.066 3.066 0 010-3.976 3.066 3.066 0 00.723-1.745 3.066 3.066 0 012.812-2.812zm7.44 5.252a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
            </svg>
            {{ content.founded }}
          </div>

          <h3 class="text-2xl font-bold text-gray-900 mb-4">{{ content.identity }}</h3>
          <p class="text-gray-600 text-lg mb-8 leading-relaxed">{{ content.description }}</p>

          <!-- Vision & Mission -->
          <div class="space-y-6">
            <div class="bg-white rounded-2xl p-6 shadow-lg border-r-4 border-[#1e3a5f]">
              <div class="flex items-start gap-4">
                <div class="w-12 h-12 bg-blue-100 rounded-xl flex items-center justify-center flex-shrink-0">
                  <svg class="w-6 h-6 text-[#1e3a5f]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z" />
                  </svg>
                </div>
                <div>
                  <h4 class="text-lg font-bold text-gray-900 mb-2">{{ content.vision }}</h4>
                  <p class="text-gray-600">{{ content.visionText }}</p>
                </div>
              </div>
            </div>

            <div class="bg-white rounded-2xl p-6 shadow-lg border-r-4 border-[#2980b9]">
              <div class="flex items-start gap-4">
                <div class="w-12 h-12 bg-cyan-100 rounded-xl flex items-center justify-center flex-shrink-0">
                  <svg class="w-6 h-6 text-[#2980b9]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
                  </svg>
                </div>
                <div>
                  <h4 class="text-lg font-bold text-gray-900 mb-2">{{ content.mission }}</h4>
                  <p class="text-gray-600">{{ content.missionText }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
