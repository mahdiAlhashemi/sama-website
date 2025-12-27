<script setup>
const props = defineProps({
  content: Object
})
</script>

<template>
  <section class="py-20 gradient-hero relative overflow-hidden">
    <!-- Background Pattern -->
    <div class="absolute inset-0 opacity-10">
      <div class="h-full w-full" style="background-image: linear-gradient(rgba(255,255,255,.1) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,.1) 1px, transparent 1px); background-size: 50px 50px;"></div>
    </div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div class="grid grid-cols-2 md:grid-cols-4 gap-8">
        <div
          v-for="(stat, index) in content.items"
          :key="index"
          class="text-center group"
        >
          <div class="relative inline-block">
            <div class="text-5xl md:text-6xl font-bold text-white mb-2 group-hover:scale-110 transition-transform">
              {{ stat.value }}
            </div>
            <div class="absolute -inset-4 bg-white/10 rounded-full blur-xl opacity-0 group-hover:opacity-100 transition-opacity"></div>
          </div>
          <div class="text-blue-200 font-medium text-lg">{{ stat.label }}</div>
        </div>
      </div>
    </div>
  </section>
</template>
