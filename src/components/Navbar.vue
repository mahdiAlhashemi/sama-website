<script setup>
import { ref } from 'vue'

const props = defineProps({
  content: Object,
  isRtl: Boolean,
  currentLang: String
})

const emit = defineEmits(['toggle-lang'])

const isMenuOpen = ref(false)
const isScrolled = ref(false)

if (typeof window !== 'undefined') {
  window.addEventListener('scroll', () => {
    isScrolled.value = window.scrollY > 50
  })
}
</script>

<template>
  <nav
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-300',
      isScrolled ? 'bg-white/95 backdrop-blur-md shadow-lg py-2' : 'bg-transparent py-4'
    ]"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between">
        <!-- Logo -->
        <div class="flex items-center gap-3">
          <div class="w-12 h-12 rounded-xl gradient-primary flex items-center justify-center">
            <span class="text-white font-bold text-xl">س</span>
          </div>
          <div>
            <h1 :class="['font-bold text-lg', isScrolled ? 'text-gray-900' : 'text-white']">
              {{ isRtl ? 'سما أرض الفرات' : 'Sama Ard Al-Furat' }}
            </h1>
          </div>
        </div>

        <!-- Desktop Navigation -->
        <div class="hidden md:flex items-center gap-8">
          <a
            v-for="(item, key) in content"
            :key="key"
            :href="`#${key}`"
            :class="[
              'font-medium transition-colors hover:text-blue-500',
              isScrolled ? 'text-gray-700' : 'text-white/90'
            ]"
          >
            {{ item }}
          </a>
        </div>

        <!-- Language Toggle & CTA -->
        <div class="hidden md:flex items-center gap-4">
          <button
            @click="emit('toggle-lang')"
            :class="[
              'px-4 py-2 rounded-lg font-medium transition-all',
              isScrolled
                ? 'bg-gray-100 text-gray-700 hover:bg-gray-200'
                : 'bg-white/10 text-white hover:bg-white/20'
            ]"
          >
            {{ currentLang === 'ar' ? 'EN' : 'عربي' }}
          </button>
          <a
            href="#contact"
            class="btn-primary text-sm"
          >
            {{ isRtl ? 'تواصل معنا' : 'Contact Us' }}
          </a>
        </div>

        <!-- Mobile Menu Button -->
        <button
          @click="isMenuOpen = !isMenuOpen"
          class="md:hidden p-2"
          :class="isScrolled ? 'text-gray-900' : 'text-white'"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path v-if="!isMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
            <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>

      <!-- Mobile Menu -->
      <div
        v-show="isMenuOpen"
        class="md:hidden mt-4 pb-4 border-t border-white/10"
      >
        <div class="flex flex-col gap-4 pt-4">
          <a
            v-for="(item, key) in content"
            :key="key"
            :href="`#${key}`"
            @click="isMenuOpen = false"
            :class="[
              'font-medium py-2',
              isScrolled ? 'text-gray-700' : 'text-white'
            ]"
          >
            {{ item }}
          </a>
          <button
            @click="emit('toggle-lang')"
            class="text-start py-2 font-medium"
            :class="isScrolled ? 'text-gray-700' : 'text-white'"
          >
            {{ currentLang === 'ar' ? 'English' : 'عربي' }}
          </button>
        </div>
      </div>
    </div>
  </nav>
</template>
