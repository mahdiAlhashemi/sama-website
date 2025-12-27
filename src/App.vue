<script setup>
import { ref, computed, onMounted } from 'vue'

const isRtl = ref(true)
const currentLang = ref('ar')
const isMenuOpen = ref(false)
const isScrolled = ref(false)
const activeService = ref(0)

const toggleLanguage = () => {
  isRtl.value = !isRtl.value
  currentLang.value = isRtl.value ? 'ar' : 'en'
  document.documentElement.dir = isRtl.value ? 'rtl' : 'ltr'
}

const content = computed(() => currentLang.value === 'ar' ? arContent : enContent)

const arContent = {
  nav: {
    home: 'الرئيسية',
    about: 'من نحن',
    services: 'خدماتنا',
    partners: 'شركاؤنا',
    contact: 'تواصل معنا'
  },
  hero: {
    title: 'سما أرض الفرات',
    subtitle: 'شريكك التكنولوجي والإنشائي بثقة عراقية',
    slogan: 'الابتكار التقني + الكفاءة الهندسية = الحلول الشاملة',
    welcome: 'نورتونا في سما أرض الفرات.. خادمين للطيبين، جئنا لنسخر أحدث التكنولوجيا ونبني الأرض بأيادي عراقية وخبرات عالمية متقدمة',
    cta1: 'استكشف حلول Odoo ERP',
    cta2: 'اطلب عرض توضيحي مجاني',
    cta3: 'تواصل مع فريقنا'
  },
  about: {
    title: 'من نحن',
    identity: 'شركة عراقية رائدة متخصصة في التكنولوجيا والمقاولات',
    founded: 'تأسست عام 2012',
    description: 'تأسست عام 2012، برزنا كشركة رائدة في المقاولات العامة وتكنولوجيا المعلومات، وفخورون بكوننا شريكاً رسمياً لشركة Odoo العالمية في العراق. نعمل في مجالات ERP والمقاولات العامة واستقدام الكوادر والتطوير البرمجي.',
    vision: 'رؤيتنا',
    visionText: 'أن نصبح الخيار التقني والإنشائي الأول في العراق والمنطقة عبر الابتكار المستمر',
    mission: 'مهمتنا',
    missionText: 'تنفيذ مشاريع استراتيجية تساهم في تطوير البنية التحتية ورفد سوق العمل بالكوادر المؤهلة'
  },
  services: {
    title: 'خدماتنا',
    subtitle: 'نقدم مجموعة شاملة من الحلول التقنية والإنشائية',
    items: [
      {
        icon: 'computer',
        title: 'حلول Odoo ERP',
        desc: 'نوفر حلول Odoo Enterprise الكاملة مع التكييف والتدريب والدعم المستمر',
        details: ['الحسابات المالية', 'الموارد البشرية', 'المبيعات والمشتريات', 'إدارة المخزون', 'التصنيع والإنتاج'],
        image: 'https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=800'
      },
      {
        icon: 'building',
        title: 'المقاولات العامة',
        desc: 'تنفيذ مشاريع إنشائية من الدراسة الأولية وحتى التسليم مع الإشراف الهندسي الكامل',
        details: ['الدراسة الأولية', 'التصميم', 'الإشراف', 'الجودة', 'السلامة'],
        image: 'https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=800'
      },
      {
        icon: 'code',
        title: 'تطوير البرمجيات',
        desc: 'تطوير تطبيقات وحلول برمجية حسب احتياجات العميل باستخدام أحدث التقنيات',
        details: ['تطبيقات الويب', 'تطبيقات الموبايل', 'الأنظمة المخصصة'],
        image: 'https://images.unsplash.com/photo-1555066931-4365d14bab8c?w=800'
      },
      {
        icon: 'users',
        title: 'استقدام الكوادر',
        desc: 'استقدام وتدريب وتوظيف كوادر متخصصة ومؤهلة لتلبية احتياجات السوق',
        details: ['التوظيف', 'التدريب', 'إدارة الموارد البشرية'],
        image: 'https://images.unsplash.com/photo-1522071820081-009f0129c71c?w=800'
      },
      {
        icon: 'target',
        title: 'الاستشارات التقنية',
        desc: 'تقديم استشارات تقنية متقدمة لتحسين الأداء والكفاءة التشغيلية',
        details: ['تحليل الأعمال', 'التحول الرقمي', 'تحسين العمليات'],
        image: 'https://images.unsplash.com/photo-1553877522-43269d4ea984?w=800'
      }
    ]
  },
  whyUs: {
    title: 'لماذا تختار سما؟',
    items: [
      { icon: 'check', title: 'الخبرة المعتمدة', desc: 'شريك رسمي معتمد من Odoo العالمية' },
      { icon: 'wrench', title: 'الدعم المستمر', desc: 'دعم فني شامل 24/7' },
      { icon: 'briefcase', title: 'الفريق المحترف', desc: 'كوادر هندسية وتقنية متخصصة' },
      { icon: 'bolt', title: 'المرونة والتكييف', desc: 'حلول مخصصة لكل عميل' },
      { icon: 'currency', title: 'الأسعار التنافسية', desc: 'قيمة عالية بأسعار منافسة' },
      { icon: 'clock', title: 'الالتزام بالمواعيد', desc: 'تسليم في الوقت المحدد' }
    ]
  },
  partners: {
    title: 'شركاؤنا',
    odoo: 'شريك رسمي معتمد',
    odooDesc: 'منصة ERP الرائدة عالمياً'
  },
  stats: {
    items: [
      { value: '+12', label: 'سنة خبرة' },
      { value: '+500', label: 'مشروع منجز' },
      { value: '+200', label: 'عميل راضٍ' },
      { value: '24/7', label: 'دعم فني' }
    ]
  },
  contact: {
    title: 'تواصل معنا',
    subtitle: 'نسعد بالإجابة على استفساراتكم',
    email: 'Dev@Samaardalfurat.com',
    phone: '+964 781 111 8564',
    address: 'بغداد، الكرادة، شارع السعدون',
    hours: 'الأحد - الخميس',
    form: {
      name: 'الاسم الكامل',
      email: 'البريد الإلكتروني',
      phone: 'رقم الهاتف',
      company: 'صناعة الشركة',
      message: 'احتياجاتك المحددة',
      submit: 'اطلب عرضاً توضيحياً'
    },
    demo: {
      title: 'اطلب عرضاً توضيحياً مجانياً لنظام Odoo',
      desc: 'سيتواصل معك فريقنا في غضون 24 ساعة'
    }
  },
  footer: {
    rights: 'جميع الحقوق محفوظة',
    company: 'سما أرض الفرات'
  }
}

const enContent = {
  nav: {
    home: 'Home',
    about: 'About Us',
    services: 'Services',
    partners: 'Partners',
    contact: 'Contact'
  },
  hero: {
    title: 'Sama Ard Al-Furat',
    subtitle: 'Your Technology & Construction Partner with Iraqi Trust',
    slogan: 'Tech Innovation + Engineering Excellence = Complete Solutions',
    welcome: 'Welcome to Sama Ard Al-Furat.. In service of excellence, we harness cutting-edge technology and build with Iraqi expertise and global know-how',
    cta1: 'Explore Odoo ERP Solutions',
    cta2: 'Request Free Demo',
    cta3: 'Contact Our Team'
  },
  about: {
    title: 'About Us',
    identity: 'A leading Iraqi company specializing in technology and construction',
    founded: 'Founded in 2012',
    description: 'Established in 2012 as a leader in contracting and IT, we are proud to be the official Odoo partner in Iraq. Operating in ERP, General Contracting, Manpower Recruitment & Software Development.',
    vision: 'Our Vision',
    visionText: 'To become the first choice for technology and construction in Iraq and the region through continuous innovation',
    mission: 'Our Mission',
    missionText: 'Executing strategic projects that contribute to infrastructure development and supplying the market with qualified personnel'
  },
  services: {
    title: 'Our Services',
    subtitle: 'We provide comprehensive technical and construction solutions',
    items: [
      {
        icon: 'computer',
        title: 'Odoo ERP Solutions',
        desc: 'Complete Odoo Enterprise solutions with customization, training & ongoing support',
        details: ['Accounting', 'HR', 'Sales & Procurement', 'Inventory Management', 'Manufacturing'],
        image: 'https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=800'
      },
      {
        icon: 'building',
        title: 'General Contracting',
        desc: 'Construction projects from initial study to handover with complete engineering supervision',
        details: ['Initial Study', 'Design', 'Supervision', 'Quality', 'Safety'],
        image: 'https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=800'
      },
      {
        icon: 'code',
        title: 'Software Development',
        desc: 'Custom software applications using latest technologies and professional methodologies',
        details: ['Web Apps', 'Mobile Apps', 'Custom Systems'],
        image: 'https://images.unsplash.com/photo-1555066931-4365d14bab8c?w=800'
      },
      {
        icon: 'users',
        title: 'Manpower Recruitment',
        desc: 'Recruiting, training & deploying specialized personnel to meet market needs',
        details: ['Recruitment', 'Training', 'HR Management'],
        image: 'https://images.unsplash.com/photo-1522071820081-009f0129c71c?w=800'
      },
      {
        icon: 'target',
        title: 'Technical Consulting',
        desc: 'Advanced technical consultations to improve organizational performance',
        details: ['Business Analysis', 'Digital Transformation', 'Process Improvement'],
        image: 'https://images.unsplash.com/photo-1553877522-43269d4ea984?w=800'
      }
    ]
  },
  whyUs: {
    title: 'Why Choose Sama?',
    items: [
      { icon: 'check', title: 'Certified Expertise', desc: 'Official certified Odoo partner' },
      { icon: 'wrench', title: 'Continuous Support', desc: 'Comprehensive 24/7 support' },
      { icon: 'briefcase', title: 'Professional Team', desc: 'Specialized engineering & technical personnel' },
      { icon: 'bolt', title: 'Flexibility', desc: 'Customized solutions for each client' },
      { icon: 'currency', title: 'Competitive Pricing', desc: 'Excellent value at competitive pricing' },
      { icon: 'clock', title: 'On-time Delivery', desc: 'On-time project delivery' }
    ]
  },
  partners: {
    title: 'Our Partners',
    odoo: 'Official Certified Partner',
    odooDesc: 'World Leading ERP Platform'
  },
  stats: {
    items: [
      { value: '+12', label: 'Years Experience' },
      { value: '+500', label: 'Projects Completed' },
      { value: '+200', label: 'Happy Clients' },
      { value: '24/7', label: 'Support' }
    ]
  },
  contact: {
    title: 'Contact Us',
    subtitle: 'We are happy to answer your inquiries',
    email: 'Dev@Samaardalfurat.com',
    phone: '+964 781 111 8564',
    address: 'Baghdad, Al-Karrada, Al-Saadoun Street',
    hours: 'Sunday - Thursday',
    form: {
      name: 'Full Name',
      email: 'Email Address',
      phone: 'Phone Number',
      company: 'Company Industry',
      message: 'Specific Needs',
      submit: 'Request Demo'
    },
    demo: {
      title: 'Request a Free Odoo Demo',
      desc: 'Our team will contact you within 24 hours'
    }
  },
  footer: {
    rights: 'All Rights Reserved',
    company: 'Sama Ard Al-Furat'
  }
}

if (typeof window !== 'undefined') {
  window.addEventListener('scroll', () => {
    isScrolled.value = window.scrollY > 50
  })
}

onMounted(() => {
  document.documentElement.dir = 'rtl'
  document.documentElement.lang = 'ar'
})

const submitForm = () => {
  alert(isRtl.value ? 'شكراً لتواصلك! سيتواصل معك فريقنا في غضون 24 ساعة' : 'Thank you! Our team will contact you within 24 hours')
}
</script>

<template>
  <div :dir="isRtl ? 'rtl' : 'ltr'" class="min-h-screen bg-[#0a0a0f]">
    <!-- Navbar -->
    <nav :class="['fixed top-0 left-0 right-0 z-50 transition-all duration-500', isScrolled ? 'bg-[#0a0a0f]/95 backdrop-blur-xl shadow-2xl shadow-[#41a632]/5 py-3' : 'bg-transparent py-5']">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between">
          <!-- Logo -->
          <div class="flex items-center gap-4">
            <div class="relative">
              <div class="absolute inset-0 bg-[#41a632] blur-xl opacity-50"></div>
              <img src="https://samaardalfurat.com/wp-content/themes/gvn/assets/img/logo.png" alt="Sama Logo" class="h-14 w-auto relative z-10" />
            </div>
          </div>

          <!-- Desktop Nav -->
          <div class="hidden lg:flex items-center gap-1">
            <a v-for="(item, key) in content.nav" :key="key" :href="`#${key}`" class="px-5 py-2.5 text-gray-300 hover:text-white font-medium transition-all hover:bg-white/5 rounded-xl">{{ item }}</a>
          </div>

          <!-- Language & CTA -->
          <div class="hidden md:flex items-center gap-4">
            <button @click="toggleLanguage" class="px-4 py-2.5 rounded-xl font-medium transition-all bg-white/5 text-gray-300 hover:bg-white/10 hover:text-white border border-white/10">
              {{ currentLang === 'ar' ? 'EN' : 'عربي' }}
            </button>
            <a href="#contact" class="btn-primary">
              <span class="relative z-10">{{ content.hero.cta3 }}</span>
            </a>
          </div>

          <!-- Mobile Menu -->
          <button @click="isMenuOpen = !isMenuOpen" class="lg:hidden p-2.5 text-white bg-white/5 rounded-xl">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
            </svg>
          </button>
        </div>

        <!-- Mobile Menu Panel -->
        <div v-show="isMenuOpen" class="lg:hidden mt-4 pb-4 glass rounded-2xl p-6">
          <div class="flex flex-col gap-2">
            <a v-for="(item, key) in content.nav" :key="key" :href="`#${key}`" @click="isMenuOpen = false" class="font-medium text-gray-300 hover:text-white py-3 px-4 hover:bg-white/5 rounded-xl transition-all">{{ item }}</a>
            <hr class="border-white/10 my-2">
            <button @click="toggleLanguage" class="text-start font-medium text-gray-300 py-3 px-4">{{ currentLang === 'ar' ? 'English' : 'عربي' }}</button>
            <a href="#contact" class="btn-primary text-center justify-center mt-2">{{ content.hero.cta3 }}</a>
          </div>
        </div>
      </div>
    </nav>

    <!-- Hero Section - Unique Tech/Enterprise Design -->
    <section id="home" class="relative min-h-screen flex items-center overflow-hidden">
      <!-- Background Image -->
      <div class="absolute inset-0">
        <img src="https://images.unsplash.com/photo-1497366216548-37526070297c?w=1920" alt="Modern Office" class="w-full h-full object-cover opacity-20" />
        <div class="absolute inset-0 bg-gradient-to-br from-[#0a0a0f] via-[#0a0a0f]/95 to-[#041f0e]"></div>
      </div>

      <!-- Animated Grid -->
      <div class="absolute inset-0 opacity-20">
        <div class="absolute inset-0" style="background-image: linear-gradient(rgba(65, 166, 50, 0.1) 1px, transparent 1px), linear-gradient(90deg, rgba(65, 166, 50, 0.1) 1px, transparent 1px); background-size: 60px 60px;"></div>
      </div>

      <!-- Floating Elements -->
      <div class="absolute top-1/4 left-10 w-96 h-96 bg-[#41a632]/20 rounded-full blur-[120px] animate-float"></div>
      <div class="absolute bottom-1/4 right-10 w-80 h-80 bg-[#00d4aa]/15 rounded-full blur-[100px] animate-float" style="animation-delay: 2s;"></div>

      <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pt-32 pb-20">
        <div class="grid lg:grid-cols-2 gap-16 items-center">
          <div class="animate-fade-in">
            <!-- Badge -->
            <div class="inline-flex items-center gap-3 bg-[#41a632]/10 backdrop-blur-sm px-5 py-2.5 rounded-full mb-8 border border-[#41a632]/30">
              <div class="w-2.5 h-2.5 bg-[#41a632] rounded-full animate-pulse"></div>
              <span class="text-[#41a632] font-semibold text-sm tracking-wide">{{ isRtl ? 'شريك Odoo الرسمي في العراق' : 'Official Odoo Partner in Iraq' }}</span>
            </div>

            <h1 class="text-5xl md:text-6xl lg:text-7xl font-black text-white mb-6 leading-[1.1]">
              {{ content.hero.title }}
            </h1>

            <h2 class="text-2xl md:text-3xl font-bold text-gradient mb-6">{{ content.hero.subtitle }}</h2>

            <div class="bg-white/5 backdrop-blur-sm border border-white/10 rounded-2xl p-5 mb-8">
              <p class="text-[#41a632] font-bold text-lg mb-2">{{ content.hero.slogan }}</p>
              <p class="text-gray-400 leading-relaxed">{{ content.hero.welcome }}</p>
            </div>

            <div class="flex flex-wrap gap-4">
              <a href="#services" class="btn-primary group">
                <svg class="w-5 h-5 group-hover:rotate-12 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" /></svg>
                {{ content.hero.cta1 }}
              </a>
              <a href="#contact" class="btn-white group">
                <svg class="w-5 h-5 group-hover:scale-110 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z" /></svg>
                {{ content.hero.cta2 }}
              </a>
            </div>
          </div>

          <!-- Hero Visual -->
          <div class="hidden lg:block">
            <div class="relative">
              <!-- Main Image Card -->
              <div class="relative rounded-3xl overflow-hidden shadow-2xl shadow-[#41a632]/20 animate-glow">
                <img src="https://images.unsplash.com/photo-1460925895917-afdab827c52f?w=800" alt="Tech Dashboard" class="w-full h-[500px] object-cover" />
                <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0f] via-transparent to-transparent"></div>

                <!-- Floating Stats Cards -->
                <div class="absolute bottom-6 left-6 right-6 glass rounded-2xl p-5">
                  <div class="grid grid-cols-4 gap-4 text-center">
                    <div v-for="(stat, i) in content.stats.items" :key="i">
                      <div class="text-2xl font-black text-[#41a632]">{{ stat.value }}</div>
                      <div class="text-xs text-gray-400">{{ stat.label }}</div>
                    </div>
                  </div>
                </div>
              </div>

              <!-- Floating Badge -->
              <div class="absolute -top-6 -right-6 glass rounded-2xl p-4 animate-float">
                <div class="flex items-center gap-3">
                  <div class="w-12 h-12 bg-[#714B67] rounded-xl flex items-center justify-center">
                    <img src="https://odoocdn.com/openerp_website/static/src/img/assets/png/odoo_logo_white.png" alt="Odoo" class="h-6 w-auto" />
                  </div>
                  <div class="text-white">
                    <div class="font-bold text-sm">Odoo Partner</div>
                    <div class="text-xs text-gray-400">Official</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Scroll Indicator -->
      <div class="absolute bottom-8 left-1/2 -translate-x-1/2">
        <div class="w-6 h-10 border-2 border-white/30 rounded-full flex items-start justify-center p-1.5">
          <div class="w-1.5 h-3 bg-[#41a632] rounded-full animate-bounce"></div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-32 relative overflow-hidden">
      <div class="absolute inset-0 gradient-mesh opacity-50"></div>

      <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-20">
          <span class="inline-flex items-center gap-2 px-5 py-2 bg-[#41a632]/10 text-[#41a632] rounded-full text-sm font-bold mb-6 border border-[#41a632]/30">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" /></svg>
            {{ isRtl ? 'تعرف علينا' : 'Get to Know Us' }}
          </span>
          <h2 class="text-4xl md:text-5xl font-black text-white mb-4">{{ content.about.title }}</h2>
          <p class="text-xl text-[#41a632] font-semibold">{{ content.about.identity }}</p>
        </div>

        <div class="grid lg:grid-cols-2 gap-16 items-center">
          <!-- Image Grid -->
          <div class="relative">
            <div class="grid grid-cols-2 gap-4">
              <div class="space-y-4">
                <div class="rounded-2xl overflow-hidden h-48 shadow-xl">
                  <img src="https://images.unsplash.com/photo-1573164713714-d95e436ab8d6?w=500" alt="Team Meeting" class="w-full h-full object-cover hover:scale-110 transition-transform duration-500" />
                </div>
                <div class="rounded-2xl overflow-hidden h-64 shadow-xl">
                  <img src="https://images.unsplash.com/photo-1504384308090-c894fdcc538d?w=500" alt="Modern Office" class="w-full h-full object-cover hover:scale-110 transition-transform duration-500" />
                </div>
              </div>
              <div class="space-y-4 pt-8">
                <div class="rounded-2xl overflow-hidden h-64 shadow-xl">
                  <img src="https://images.unsplash.com/photo-1581091226825-a6a2a5aee158?w=500" alt="Tech Work" class="w-full h-full object-cover hover:scale-110 transition-transform duration-500" />
                </div>
                <div class="rounded-2xl overflow-hidden h-48 shadow-xl">
                  <img src="https://images.unsplash.com/photo-1541746972996-4e0b0f43e02a?w=500" alt="Construction" class="w-full h-full object-cover hover:scale-110 transition-transform duration-500" />
                </div>
              </div>
            </div>

            <!-- Experience Badge -->
            <div class="absolute -bottom-6 left-1/2 -translate-x-1/2 glass-light rounded-2xl p-5 shadow-xl">
              <div class="flex items-center gap-4">
                <div class="w-16 h-16 bg-gradient-to-br from-[#41a632] to-[#00d4aa] rounded-xl flex items-center justify-center text-white font-black text-2xl">12+</div>
                <div>
                  <div class="font-bold text-gray-900">{{ content.about.founded }}</div>
                  <div class="text-sm text-gray-500">{{ isRtl ? 'من الخبرة والإنجاز' : 'of Excellence' }}</div>
                </div>
              </div>
            </div>
          </div>

          <!-- Content -->
          <div>
            <p class="text-gray-400 text-lg leading-relaxed mb-10">{{ content.about.description }}</p>

            <div class="space-y-6">
              <div class="glass rounded-2xl p-6 border-r-4 border-[#41a632] hover:bg-white/10 transition-all group">
                <div class="flex items-center gap-4 mb-3">
                  <div class="w-12 h-12 bg-[#41a632]/20 rounded-xl flex items-center justify-center group-hover:bg-[#41a632]/30 transition-colors">
                    <svg class="w-6 h-6 text-[#41a632]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" /><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z" /></svg>
                  </div>
                  <h4 class="text-xl font-bold text-white">{{ content.about.vision }}</h4>
                </div>
                <p class="text-gray-400">{{ content.about.visionText }}</p>
              </div>

              <div class="glass rounded-2xl p-6 border-r-4 border-[#00d4aa] hover:bg-white/10 transition-all group">
                <div class="flex items-center gap-4 mb-3">
                  <div class="w-12 h-12 bg-[#00d4aa]/20 rounded-xl flex items-center justify-center group-hover:bg-[#00d4aa]/30 transition-colors">
                    <svg class="w-6 h-6 text-[#00d4aa]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" /></svg>
                  </div>
                  <h4 class="text-xl font-bold text-white">{{ content.about.mission }}</h4>
                </div>
                <p class="text-gray-400">{{ content.about.missionText }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Services Section - Interactive Tab Design -->
    <section id="services" class="py-32 bg-[#0d0d12]">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <span class="inline-flex items-center gap-2 px-5 py-2 bg-[#41a632]/10 text-[#41a632] rounded-full text-sm font-bold mb-6 border border-[#41a632]/30">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z" /></svg>
            {{ isRtl ? 'ما نقدمه' : 'What We Offer' }}
          </span>
          <h2 class="text-4xl md:text-5xl font-black text-white mb-4">{{ content.services.title }}</h2>
          <p class="text-xl text-gray-400 max-w-2xl mx-auto">{{ content.services.subtitle }}</p>
        </div>

        <!-- Service Tabs -->
        <div class="flex flex-wrap justify-center gap-3 mb-12">
          <button
            v-for="(service, i) in content.services.items"
            :key="i"
            @click="activeService = i"
            :class="['px-6 py-3 rounded-xl font-semibold transition-all', activeService === i ? 'bg-[#41a632] text-white shadow-lg shadow-[#41a632]/30' : 'bg-white/5 text-gray-400 hover:bg-white/10 hover:text-white']"
          >
            {{ service.title }}
          </button>
        </div>

        <!-- Active Service Display -->
        <div class="grid lg:grid-cols-2 gap-12 items-center">
          <div class="relative rounded-3xl overflow-hidden h-[500px] shadow-2xl">
            <img :src="content.services.items[activeService].image" :alt="content.services.items[activeService].title" class="w-full h-full object-cover" />
            <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0f] via-[#0a0a0f]/50 to-transparent"></div>
          </div>

          <div class="glass rounded-3xl p-10">
            <div class="w-20 h-20 bg-gradient-to-br from-[#41a632] to-[#00d4aa] rounded-2xl flex items-center justify-center mb-8 text-white shadow-xl shadow-[#41a632]/30">
              <svg v-if="content.services.items[activeService].icon === 'computer'" class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 17.25v1.007a3 3 0 0 1-.879 2.122L7.5 21h9l-.621-.621A3 3 0 0 1 15 18.257V17.25m6-12V15a2.25 2.25 0 0 1-2.25 2.25H5.25A2.25 2.25 0 0 1 3 15V5.25m18 0A2.25 2.25 0 0 0 18.75 3H5.25A2.25 2.25 0 0 0 3 5.25m18 0V12a2.25 2.25 0 0 1-2.25 2.25H5.25A2.25 2.25 0 0 1 3 12V5.25" /></svg>
              <svg v-else-if="content.services.items[activeService].icon === 'building'" class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M2.25 21h19.5m-18-18v18m10.5-18v18m6-13.5V21M6.75 6.75h.75m-.75 3h.75m-.75 3h.75m3-6h.75m-.75 3h.75m-.75 3h.75M6.75 21v-3.375c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125V21M3 3h12m-.75 4.5H21m-3.75 3.75h.008v.008h-.008v-.008Zm0 3h.008v.008h-.008v-.008Zm0 3h.008v.008h-.008v-.008Z" /></svg>
              <svg v-else-if="content.services.items[activeService].icon === 'code'" class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17.25 6.75 22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3-4.5 16.5" /></svg>
              <svg v-else-if="content.services.items[activeService].icon === 'users'" class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M15 19.128a9.38 9.38 0 0 0 2.625.372 9.337 9.337 0 0 0 4.121-.952 4.125 4.125 0 0 0-7.533-2.493M15 19.128v-.003c0-1.113-.285-2.16-.786-3.07M15 19.128v.106A12.318 12.318 0 0 1 8.624 21c-2.331 0-4.512-.645-6.374-1.766l-.001-.109a6.375 6.375 0 0 1 11.964-3.07M12 6.375a3.375 3.375 0 1 1-6.75 0 3.375 3.375 0 0 1 6.75 0Zm8.25 2.25a2.625 2.625 0 1 1-5.25 0 2.625 2.625 0 0 1 5.25 0Z" /></svg>
              <svg v-else class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 21a9.004 9.004 0 0 0 8.716-6.747M12 21a9.004 9.004 0 0 1-8.716-6.747M12 21c2.485 0 4.5-4.03 4.5-9S14.485 3 12 3m0 18c-2.485 0-4.5-4.03-4.5-9S9.515 3 12 3m0 0a8.997 8.997 0 0 1 7.843 4.582M12 3a8.997 8.997 0 0 0-7.843 4.582m15.686 0A11.953 11.953 0 0 1 12 10.5c-2.998 0-5.74-1.1-7.843-2.918m15.686 0A8.959 8.959 0 0 1 21 12c0 .778-.099 1.533-.284 2.253m0 0A17.919 17.919 0 0 1 12 16.5c-3.162 0-6.133-.815-8.716-2.247m0 0A9.015 9.015 0 0 1 3 12c0-1.605.42-3.113 1.157-4.418" /></svg>
            </div>

            <h3 class="text-3xl font-bold text-white mb-4">{{ content.services.items[activeService].title }}</h3>
            <p class="text-gray-400 text-lg leading-relaxed mb-8">{{ content.services.items[activeService].desc }}</p>

            <div class="flex flex-wrap gap-3">
              <span v-for="(detail, j) in content.services.items[activeService].details" :key="j" class="px-4 py-2 bg-[#41a632]/10 text-[#41a632] rounded-xl font-medium border border-[#41a632]/30">
                {{ detail }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Why Us Section -->
    <section class="py-32 relative overflow-hidden">
      <div class="absolute inset-0 gradient-mesh opacity-30"></div>

      <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-4xl md:text-5xl font-black text-white mb-4">{{ content.whyUs.title }}</h2>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div v-for="(item, i) in content.whyUs.items" :key="i" class="glass rounded-2xl p-8 card-hover group">
            <div class="w-16 h-16 bg-gradient-to-br from-[#41a632] to-[#00d4aa] rounded-2xl flex items-center justify-center mb-6 text-white group-hover:scale-110 transition-transform shadow-lg shadow-[#41a632]/20">
              <svg v-if="item.icon === 'check'" class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12.75 11.25 15 15 9.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" /></svg>
              <svg v-else-if="item.icon === 'wrench'" class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11.42 15.17 17.25 21A2.652 2.652 0 0 0 21 17.25l-5.877-5.877M11.42 15.17l2.496-3.03c.317-.384.74-.626 1.208-.766M11.42 15.17l-4.655 5.653a2.548 2.548 0 1 1-3.586-3.586l6.837-5.63m5.108-.233c.55-.164 1.163-.188 1.743-.14a4.5 4.5 0 0 0 4.486-6.336l-3.276 3.277a3.004 3.004 0 0 1-2.25-2.25l3.276-3.276a4.5 4.5 0 0 0-6.336 4.486c.091 1.076-.071 2.264-.904 2.95l-.102.085m-1.745 1.437L5.909 7.5H4.5L2.25 3.75l1.5-1.5L7.5 4.5v1.409l4.26 4.26m-1.745 1.437 1.745-1.437m6.615 8.206L15.75 15.75M4.867 19.125h.008v.008h-.008v-.008Z" /></svg>
              <svg v-else-if="item.icon === 'briefcase'" class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.25 14.15v4.25c0 1.094-.787 2.036-1.872 2.18-2.087.277-4.216.42-6.378.42s-4.291-.143-6.378-.42c-1.085-.144-1.872-1.086-1.872-2.18v-4.25m16.5 0a2.18 2.18 0 0 0 .75-1.661V8.706c0-1.081-.768-2.015-1.837-2.175a48.114 48.114 0 0 0-3.413-.387m4.5 8.006c-.194.165-.42.295-.673.38A23.978 23.978 0 0 1 12 15.75c-2.648 0-5.195-.429-7.577-1.22a2.016 2.016 0 0 1-.673-.38m0 0A2.18 2.18 0 0 1 3 12.489V8.706c0-1.081.768-2.015 1.837-2.175a48.111 48.111 0 0 1 3.413-.387m7.5 0V5.25A2.25 2.25 0 0 0 13.5 3h-3a2.25 2.25 0 0 0-2.25 2.25v.894m7.5 0a48.667 48.667 0 0 0-7.5 0M12 12.75h.008v.008H12v-.008Z" /></svg>
              <svg v-else-if="item.icon === 'bolt'" class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m3.75 13.5 10.5-11.25L12 10.5h8.25L9.75 21.75 12 13.5H3.75Z" /></svg>
              <svg v-else-if="item.icon === 'currency'" class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v12m-3-2.818.879.659c1.171.879 3.07.879 4.242 0 1.172-.879 1.172-2.303 0-3.182C13.536 12.219 12.768 12 12 12c-.725 0-1.45-.22-2.003-.659-1.106-.879-1.106-2.303 0-3.182s2.9-.879 4.006 0l.415.33M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" /></svg>
              <svg v-else class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6h4.5m4.5 0a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" /></svg>
            </div>
            <h3 class="text-xl font-bold text-white mb-3">{{ item.title }}</h3>
            <p class="text-gray-400">{{ item.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Partners Section -->
    <section id="partners" class="py-32 bg-[#0d0d12]">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-4xl md:text-5xl font-black text-white mb-4">{{ content.partners.title }}</h2>
        </div>

        <div class="max-w-3xl mx-auto">
          <div class="relative overflow-hidden rounded-3xl">
            <img src="https://images.unsplash.com/photo-1552664730-d307ca884978?w=1200" alt="Partnership" class="w-full h-80 object-cover opacity-30" />
            <div class="absolute inset-0 bg-gradient-to-r from-[#714B67] to-[#8f5f7f]"></div>
            <div class="absolute inset-0 flex flex-col items-center justify-center text-white text-center p-8">
              <div class="w-24 h-24 bg-white rounded-2xl flex items-center justify-center mb-6 shadow-2xl">
                <img src="https://odoocdn.com/openerp_website/static/src/img/assets/png/odoo_logo.png" alt="Odoo Logo" class="h-12 w-auto" />
              </div>
              <h3 class="text-3xl font-bold mb-3">{{ content.partners.odoo }}</h3>
              <p class="text-white/80 text-lg mb-6">{{ content.partners.odooDesc }}</p>
              <div class="flex flex-wrap justify-center gap-3">
                <span class="px-5 py-2 bg-white/20 rounded-full text-sm font-medium">ERP Solutions</span>
                <span class="px-5 py-2 bg-white/20 rounded-full text-sm font-medium">CRM</span>
                <span class="px-5 py-2 bg-white/20 rounded-full text-sm font-medium">HR Management</span>
                <span class="px-5 py-2 bg-white/20 rounded-full text-sm font-medium">Accounting</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-32 relative overflow-hidden">
      <div class="absolute inset-0 gradient-mesh opacity-30"></div>

      <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <span class="inline-flex items-center gap-2 px-5 py-2 bg-[#41a632]/10 text-[#41a632] rounded-full text-sm font-bold mb-6 border border-[#41a632]/30">
            {{ isRtl ? 'تواصل معنا' : 'Get in Touch' }}
          </span>
          <h2 class="text-4xl md:text-5xl font-black text-white mb-4">{{ content.contact.title }}</h2>
          <p class="text-xl text-gray-400">{{ content.contact.subtitle }}</p>
        </div>

        <div class="grid lg:grid-cols-2 gap-12 max-w-6xl mx-auto">
          <!-- Contact Info -->
          <div class="glass rounded-3xl p-10 relative overflow-hidden">
            <div class="absolute top-0 right-0 w-64 h-64 bg-[#41a632]/10 rounded-full blur-3xl"></div>
            <div class="relative z-10">
              <h3 class="text-2xl font-bold text-white mb-8">{{ isRtl ? 'معلومات التواصل' : 'Contact Info' }}</h3>

              <div class="space-y-6">
                <div class="flex items-center gap-5 group">
                  <div class="w-14 h-14 bg-[#41a632]/20 rounded-xl flex items-center justify-center group-hover:bg-[#41a632]/30 transition-colors">
                    <svg class="w-6 h-6 text-[#41a632]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21.75 6.75v10.5a2.25 2.25 0 0 1-2.25 2.25h-15a2.25 2.25 0 0 1-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0 0 19.5 4.5h-15a2.25 2.25 0 0 0-2.25 2.25m19.5 0v.243a2.25 2.25 0 0 1-1.07 1.916l-7.5 4.615a2.25 2.25 0 0 1-2.36 0L3.32 8.91a2.25 2.25 0 0 1-1.07-1.916V6.75" /></svg>
                  </div>
                  <div>
                    <div class="text-gray-500 text-sm mb-1">{{ isRtl ? 'البريد الإلكتروني' : 'Email' }}</div>
                    <div class="text-white font-semibold">{{ content.contact.email }}</div>
                  </div>
                </div>

                <div class="flex items-center gap-5 group">
                  <div class="w-14 h-14 bg-[#41a632]/20 rounded-xl flex items-center justify-center group-hover:bg-[#41a632]/30 transition-colors">
                    <svg class="w-6 h-6 text-[#41a632]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 0 0 2.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-.282.376-.769.542-1.21.38a12.035 12.035 0 0 1-7.143-7.143c-.162-.441.004-.928.38-1.21l1.293-.97c.363-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 0 0-1.091-.852H4.5A2.25 2.25 0 0 0 2.25 4.5v2.25Z" /></svg>
                  </div>
                  <div>
                    <div class="text-gray-500 text-sm mb-1">{{ isRtl ? 'الهاتف' : 'Phone' }}</div>
                    <div class="text-white font-semibold" dir="ltr">{{ content.contact.phone }}</div>
                  </div>
                </div>

                <div class="flex items-center gap-5 group">
                  <div class="w-14 h-14 bg-[#41a632]/20 rounded-xl flex items-center justify-center group-hover:bg-[#41a632]/30 transition-colors">
                    <svg class="w-6 h-6 text-[#41a632]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M15 10.5a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z" /><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1 1 15 0Z" /></svg>
                  </div>
                  <div>
                    <div class="text-gray-500 text-sm mb-1">{{ isRtl ? 'العنوان' : 'Address' }}</div>
                    <div class="text-white font-semibold">{{ content.contact.address }}</div>
                  </div>
                </div>

                <div class="flex items-center gap-5 group">
                  <div class="w-14 h-14 bg-[#41a632]/20 rounded-xl flex items-center justify-center group-hover:bg-[#41a632]/30 transition-colors">
                    <svg class="w-6 h-6 text-[#41a632]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 6v6h4.5m4.5 0a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" /></svg>
                  </div>
                  <div>
                    <div class="text-gray-500 text-sm mb-1">{{ isRtl ? 'ساعات العمل' : 'Working Hours' }}</div>
                    <div class="text-white font-semibold">{{ content.contact.hours }}</div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <!-- Contact Form -->
          <div class="glass-light rounded-3xl p-10 shadow-2xl">
            <div class="text-center mb-8">
              <h4 class="text-2xl font-bold text-gray-900">{{ content.contact.demo.title }}</h4>
              <p class="text-gray-500 mt-2">{{ content.contact.demo.desc }}</p>
            </div>
            <form @submit.prevent="submitForm" class="space-y-5">
              <div>
                <label class="block text-sm font-semibold text-gray-700 mb-2">{{ content.contact.form.name }}</label>
                <input type="text" required class="w-full px-5 py-4 rounded-xl border border-gray-200 focus:border-[#41a632] focus:ring-4 focus:ring-[#41a632]/10 outline-none transition-all bg-gray-50" />
              </div>
              <div class="grid md:grid-cols-2 gap-5">
                <div>
                  <label class="block text-sm font-semibold text-gray-700 mb-2">{{ content.contact.form.email }}</label>
                  <input type="email" required class="w-full px-5 py-4 rounded-xl border border-gray-200 focus:border-[#41a632] focus:ring-4 focus:ring-[#41a632]/10 outline-none transition-all bg-gray-50" />
                </div>
                <div>
                  <label class="block text-sm font-semibold text-gray-700 mb-2">{{ content.contact.form.phone }}</label>
                  <input type="tel" class="w-full px-5 py-4 rounded-xl border border-gray-200 focus:border-[#41a632] focus:ring-4 focus:ring-[#41a632]/10 outline-none transition-all bg-gray-50" dir="ltr" />
                </div>
              </div>
              <div>
                <label class="block text-sm font-semibold text-gray-700 mb-2">{{ content.contact.form.company }}</label>
                <input type="text" class="w-full px-5 py-4 rounded-xl border border-gray-200 focus:border-[#41a632] focus:ring-4 focus:ring-[#41a632]/10 outline-none transition-all bg-gray-50" />
              </div>
              <div>
                <label class="block text-sm font-semibold text-gray-700 mb-2">{{ content.contact.form.message }}</label>
                <textarea rows="4" class="w-full px-5 py-4 rounded-xl border border-gray-200 focus:border-[#41a632] focus:ring-4 focus:ring-[#41a632]/10 outline-none resize-none transition-all bg-gray-50"></textarea>
              </div>
              <button type="submit" class="w-full btn-primary justify-center text-lg py-5">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 12 3.269 3.125A59.769 59.769 0 0 1 21.485 12 59.768 59.768 0 0 1 3.27 20.875L5.999 12Zm0 0h7.5" /></svg>
                {{ content.contact.form.submit }}
              </button>
            </form>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-[#050508] border-t border-white/5">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Main Footer -->
        <div class="py-16 grid md:grid-cols-2 lg:grid-cols-4 gap-12">
          <!-- Company Info -->
          <div class="lg:col-span-2">
            <div class="flex items-center gap-4 mb-6">
              <img src="https://samaardalfurat.com/wp-content/themes/gvn/assets/img/logo.png" alt="Sama Logo" class="h-14 w-auto" />
              <div>
                <h3 class="text-white font-bold text-xl">{{ content.footer.company }}</h3>
                <p class="text-[#41a632] text-sm">samaardalfurat.com</p>
              </div>
            </div>
            <p class="text-gray-400 leading-relaxed mb-6 max-w-md">{{ isRtl ? 'شريكك التكنولوجي والإنشائي الموثوق في العراق. نقدم حلول Odoo ERP والمقاولات العامة والتطوير البرمجي.' : 'Your trusted technology and construction partner in Iraq. We provide Odoo ERP solutions, general contracting, and software development.' }}</p>
            <!-- Social Links -->
            <div class="flex items-center gap-3">
              <a href="https://www.facebook.com/samaardalfurat" target="_blank" class="w-11 h-11 glass rounded-xl flex items-center justify-center hover:bg-[#41a632] transition-all duration-300 group">
                <svg class="w-5 h-5 text-gray-400 group-hover:text-white transition-colors" fill="currentColor" viewBox="0 0 24 24"><path d="M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z"/></svg>
              </a>
              <a href="https://www.instagram.com/samaardalfurat" target="_blank" class="w-11 h-11 glass rounded-xl flex items-center justify-center hover:bg-[#41a632] transition-all duration-300 group">
                <svg class="w-5 h-5 text-gray-400 group-hover:text-white transition-colors" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
              </a>
              <a href="https://www.linkedin.com/company/samaardalfurat" target="_blank" class="w-11 h-11 glass rounded-xl flex items-center justify-center hover:bg-[#41a632] transition-all duration-300 group">
                <svg class="w-5 h-5 text-gray-400 group-hover:text-white transition-colors" fill="currentColor" viewBox="0 0 24 24"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/></svg>
              </a>
              <a href="https://wa.me/9647811118564" target="_blank" class="w-11 h-11 glass rounded-xl flex items-center justify-center hover:bg-[#25D366] transition-all duration-300 group">
                <svg class="w-5 h-5 text-gray-400 group-hover:text-white transition-colors" fill="currentColor" viewBox="0 0 24 24"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
              </a>
            </div>
          </div>

          <!-- Quick Links -->
          <div>
            <h4 class="text-white font-bold text-lg mb-6">{{ isRtl ? 'روابط سريعة' : 'Quick Links' }}</h4>
            <ul class="space-y-3">
              <li><a href="#home" class="text-gray-400 hover:text-[#41a632] transition-colors">{{ content.nav.home }}</a></li>
              <li><a href="#about" class="text-gray-400 hover:text-[#41a632] transition-colors">{{ content.nav.about }}</a></li>
              <li><a href="#services" class="text-gray-400 hover:text-[#41a632] transition-colors">{{ content.nav.services }}</a></li>
              <li><a href="#partners" class="text-gray-400 hover:text-[#41a632] transition-colors">{{ content.nav.partners }}</a></li>
              <li><a href="#contact" class="text-gray-400 hover:text-[#41a632] transition-colors">{{ content.nav.contact }}</a></li>
            </ul>
          </div>

          <!-- Contact Info -->
          <div>
            <h4 class="text-white font-bold text-lg mb-6">{{ isRtl ? 'تواصل معنا' : 'Contact Us' }}</h4>
            <ul class="space-y-4">
              <li class="flex items-start gap-3">
                <svg class="w-5 h-5 text-[#41a632] mt-0.5 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21.75 6.75v10.5a2.25 2.25 0 0 1-2.25 2.25h-15a2.25 2.25 0 0 1-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0 0 19.5 4.5h-15a2.25 2.25 0 0 0-2.25 2.25m19.5 0v.243a2.25 2.25 0 0 1-1.07 1.916l-7.5 4.615a2.25 2.25 0 0 1-2.36 0L3.32 8.91a2.25 2.25 0 0 1-1.07-1.916V6.75" /></svg>
                <span class="text-gray-400">{{ content.contact.email }}</span>
              </li>
              <li class="flex items-start gap-3">
                <svg class="w-5 h-5 text-[#41a632] mt-0.5 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 0 0 2.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-.282.376-.769.542-1.21.38a12.035 12.035 0 0 1-7.143-7.143c-.162-.441.004-.928.38-1.21l1.293-.97c.363-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 0 0-1.091-.852H4.5A2.25 2.25 0 0 0 2.25 4.5v2.25Z" /></svg>
                <span class="text-gray-400" dir="ltr">{{ content.contact.phone }}</span>
              </li>
              <li class="flex items-start gap-3">
                <svg class="w-5 h-5 text-[#41a632] mt-0.5 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M15 10.5a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z" /><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1 1 15 0Z" /></svg>
                <span class="text-gray-400">{{ content.contact.address }}</span>
              </li>
            </ul>
          </div>
        </div>

        <!-- Copyright -->
        <div class="py-6 border-t border-white/5 flex flex-col md:flex-row justify-between items-center gap-4">
          <p class="text-gray-500 text-sm">&copy; {{ new Date().getFullYear() }} {{ content.footer.company }}. {{ content.footer.rights }}.</p>
          <div class="flex items-center gap-2">
            <img src="https://odoocdn.com/openerp_website/static/src/img/assets/png/odoo_logo_white.png" alt="Odoo Partner" class="h-5 w-auto opacity-60" />
            <span class="text-gray-600 text-xs">Official Partner</span>
          </div>
        </div>
      </div>
    </footer>

    <!-- WhatsApp Floating Button -->
    <a href="https://wa.me/9647811118564" target="_blank" class="fixed bottom-6 right-6 z-50 w-16 h-16 bg-[#25D366] rounded-full flex items-center justify-center shadow-2xl shadow-[#25D366]/40 hover:scale-110 transition-all duration-300 group" :class="isRtl ? 'left-6 right-auto' : 'right-6'">
      <svg class="w-8 h-8 text-white" fill="currentColor" viewBox="0 0 24 24"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
      <span class="absolute -top-2 -right-2 w-5 h-5 bg-red-500 rounded-full flex items-center justify-center text-white text-xs font-bold animate-pulse">1</span>
    </a>
  </div>
</template>
