<script setup>
const props = defineProps({
  content: Object,
  isRtl: Boolean
})
</script>

<template>
  <section id="why-us" class="py-24 bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <span class="inline-block px-4 py-2 bg-green-100 text-green-700 rounded-full text-sm font-semibold mb-4">
          {{ isRtl ? 'مميزاتنا' : 'Our Advantages' }}
        </span>
        <h2 class="section-title text-gray-900">{{ content.title }}</h2>
      </div>

      <!-- Features Grid -->
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div
          v-for="(item, index) in content.items"
          :key="index"
          class="bg-white rounded-2xl p-6 shadow-md hover:shadow-xl transition-all duration-300 card-hover border border-gray-100 group"
        >
          <div class="flex items-start gap-4">
            <div class="w-14 h-14 bg-gradient-to-br from-[#1e3a5f] to-[#2980b9] rounded-2xl flex items-center justify-center text-2xl flex-shrink-0 group-hover:scale-110 transition-transform">
              {{ item.icon }}
            </div>
            <div>
              <h3 class="text-lg font-bold text-gray-900 mb-2">{{ item.title }}</h3>
              <p class="text-gray-600 text-sm leading-relaxed">{{ item.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
