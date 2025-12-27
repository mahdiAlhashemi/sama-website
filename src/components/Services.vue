<script setup>
const props = defineProps({
  content: Object,
  isRtl: Boolean
})

const iconColors = [
  'bg-blue-100 text-blue-600',
  'bg-orange-100 text-orange-600',
  'bg-purple-100 text-purple-600',
  'bg-green-100 text-green-600',
  'bg-pink-100 text-pink-600'
]
</script>

<template>
  <section id="services" class="py-24 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <span class="inline-block px-4 py-2 bg-blue-100 text-blue-700 rounded-full text-sm font-semibold mb-4">
          {{ isRtl ? 'ماذا نقدم' : 'What We Offer' }}
        </span>
        <h2 class="section-title text-gray-900">{{ content.title }}</h2>
        <p class="section-subtitle">{{ content.subtitle }}</p>
      </div>

      <!-- Services Grid -->
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="(service, index) in content.items"
          :key="index"
          class="group bg-white rounded-3xl p-8 shadow-lg hover:shadow-2xl transition-all duration-500 card-hover border border-gray-100"
        >
          <!-- Icon -->
          <div
            :class="[
              'w-16 h-16 rounded-2xl flex items-center justify-center text-3xl mb-6 transition-transform group-hover:scale-110',
              iconColors[index % iconColors.length]
            ]"
          >
            {{ service.icon }}
          </div>

          <!-- Content -->
          <h3 class="text-xl font-bold text-gray-900 mb-3 group-hover:text-[#1e3a5f] transition-colors">
            {{ service.title }}
          </h3>
          <p class="text-gray-600 mb-6 leading-relaxed">{{ service.desc }}</p>

          <!-- Details List -->
          <ul class="space-y-2">
            <li
              v-for="(detail, i) in service.details"
              :key="i"
              class="flex items-center gap-2 text-sm text-gray-500"
            >
              <svg class="w-4 h-4 text-green-500 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
              </svg>
              {{ detail }}
            </li>
          </ul>

          <!-- Arrow -->
          <div class="mt-6 pt-6 border-t border-gray-100">
            <a
              href="#contact"
              class="inline-flex items-center gap-2 text-[#1e3a5f] font-semibold group-hover:gap-4 transition-all"
            >
              {{ isRtl ? 'اعرف المزيد' : 'Learn More' }}
              <svg :class="['w-5 h-5 transition-transform', isRtl ? 'rotate-180' : '']" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
              </svg>
            </a>
          </div>
        </div>
      </div>

      <!-- CTA -->
      <div class="text-center mt-16">
        <a href="#contact" class="btn-primary text-lg">
          {{ isRtl ? 'احصل على استشارة مجانية' : 'Get Free Consultation' }}
        </a>
      </div>
    </div>
  </section>
</template>
