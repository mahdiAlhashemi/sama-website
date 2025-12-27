<script setup>
const props = defineProps({
  content: Object,
  isRtl: Boolean
})
</script>

<template>
  <section id="partners" class="py-24 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <span class="inline-block px-4 py-2 bg-purple-100 text-purple-700 rounded-full text-sm font-semibold mb-4">
          {{ isRtl ? 'شراكاتنا' : 'Our Partnerships' }}
        </span>
        <h2 class="section-title text-gray-900">{{ content.title }}</h2>
      </div>

      <!-- Odoo Partner Card -->
      <div class="max-w-3xl mx-auto">
        <div class="bg-gradient-to-br from-purple-600 to-indigo-700 rounded-3xl p-8 md:p-12 text-white relative overflow-hidden">
          <!-- Background Pattern -->
          <div class="absolute inset-0 opacity-10">
            <div class="absolute top-0 left-0 w-40 h-40 bg-white rounded-full -translate-x-1/2 -translate-y-1/2"></div>
            <div class="absolute bottom-0 right-0 w-60 h-60 bg-white rounded-full translate-x-1/2 translate-y-1/2"></div>
          </div>

          <div class="relative z-10 flex flex-col md:flex-row items-center gap-8">
            <!-- Odoo Logo -->
            <div class="bg-white rounded-2xl p-6 shadow-xl">
              <svg class="w-32 h-12" viewBox="0 0 150 50" fill="none">
                <text x="10" y="35" font-family="Arial" font-size="32" font-weight="bold" fill="#714B67">odoo</text>
              </svg>
            </div>

            <!-- Content -->
            <div class="text-center md:text-start">
              <div class="inline-flex items-center gap-2 bg-white/20 backdrop-blur-sm px-4 py-2 rounded-full text-sm font-medium mb-4">
                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M6.267 3.455a3.066 3.066 0 001.745-.723 3.066 3.066 0 013.976 0 3.066 3.066 0 001.745.723 3.066 3.066 0 012.812 2.812c.051.643.304 1.254.723 1.745a3.066 3.066 0 010 3.976 3.066 3.066 0 00-.723 1.745 3.066 3.066 0 01-2.812 2.812 3.066 3.066 0 00-1.745.723 3.066 3.066 0 01-3.976 0 3.066 3.066 0 00-1.745-.723 3.066 3.066 0 01-2.812-2.812 3.066 3.066 0 00-.723-1.745 3.066 3.066 0 010-3.976 3.066 3.066 0 00.723-1.745 3.066 3.066 0 012.812-2.812zm7.44 5.252a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
                {{ content.odoo }}
              </div>
              <h3 class="text-2xl md:text-3xl font-bold mb-3">{{ content.odooDesc }}</h3>
              <p class="text-white/80 mb-6">
                {{ isRtl ? 'نقدم حلول Odoo المتكاملة للشركات العراقية بأعلى معايير الجودة والدعم المستمر' : 'We provide complete Odoo solutions for Iraqi businesses with highest quality standards and continuous support' }}
              </p>
              <a href="#contact" class="inline-flex items-center gap-2 bg-white text-purple-700 px-6 py-3 rounded-xl font-semibold hover:bg-purple-50 transition-colors">
                {{ isRtl ? 'احصل على عرض' : 'Get a Quote' }}
                <svg :class="['w-5 h-5', isRtl ? 'rotate-180' : '']" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
                </svg>
              </a>
            </div>
          </div>
        </div>
      </div>

      <!-- Additional Partners Placeholder -->
      <div class="mt-16 text-center">
        <p class="text-gray-500 mb-8">{{ isRtl ? 'نفتخر بالعمل مع أفضل الشركات' : 'Proud to work with the best companies' }}</p>
        <div class="flex flex-wrap justify-center items-center gap-12 opacity-50">
          <div class="w-24 h-12 bg-gray-200 rounded-lg"></div>
          <div class="w-24 h-12 bg-gray-200 rounded-lg"></div>
          <div class="w-24 h-12 bg-gray-200 rounded-lg"></div>
          <div class="w-24 h-12 bg-gray-200 rounded-lg"></div>
        </div>
      </div>
    </div>
  </section>
</template>
