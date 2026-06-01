<script setup>
import { ref, onMounted } from 'vue'
import {
  CodeBracketIcon,
  EnvelopeIcon,
  DocumentTextIcon,
  ArrowDownIcon,
  SparklesIcon,
  UserIcon,
  BriefcaseIcon,
  AcademicCapIcon,
  ChatBubbleLeftRightIcon,
} from '@heroicons/vue/24/outline'

const sections = ref([
  { id: 'home', label: 'Home' },
  { id: 'skills', label: 'Skills' },
  { id: 'projects', label: 'Projects' },
  { id: 'experience', label: 'Experience' },
  { id: 'contact', label: 'Contact' },
])

const skills = ref([
  { name: 'Vue.js', level: 95, color: 'from-green-500 to-emerald-400' },
  { name: 'Wordpress', level: 85, color: 'from-yellow-500 to-amber-400' },
  { name: 'Tailwind CSS', level: 90, color: 'from-cyan-500 to-blue-400' },
  { name: 'TS', level: 50, color: 'from-purple-500 to-pink-400' },
  { name: 'Vanilla JavaScript', level: 70, color: 'from-blue-500 to-cyan-400' },
  { name: 'Nuxt', level: 83, color: 'from-green-400 to-emerald-300' },
])

const projects = ref([
  {
    title: 'Chat system',
    description: 'A fully functioning chat bot, and an admin dashbord panel built with Vue.js',
    tags: ['Vue.js', 'Tailwind CSS'],
    image: 'https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?auto=format&fit=crop&w=500',
    link: 'https://app.botconvo.com/',
  },
  {
    title: 'Inventory System',
    description:
      'An all-in-one business management system to help businesses manage sales, inventory — all in real time. PWA integration and an offline mode.',
    tags: ['Vue.js', 'Tailwind CSS', 'API', 'Chat system'],
    image:
      'https://images.unsplash.com/photo-1611224923853-80b023f02d71?auto=format&fit=crop&w=500',
    link: 'https://app.savemybusiness.com.ng/',
  },
  {
    title: 'Andre movie app',
    description:
      'A modern, responsive movie discovery web application built to explore popular, top-rated, and upcoming movies.',
    tags: ['Vue.js', 'API', 'Tailwind CSS'],
    image:
      'https://images.unsplash.com/photo-1535016120720-40c646be5580?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8OHx8bW92aWV8ZW58MHx8MHx8fDA%3D',
    link: 'https://andre-movie-production.netlify.app/',
  },
  {
    title: 'Disablity aid solutions',
    description:
      'An E-commerce platform built to provide assistive devices and resources for individuals with disabilities.',
    tags: ['Wordpress', 'WooCommerce'],
    image:
      'https://images.unsplash.com/photo-1723433892471-62f113c8c9a0?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8RGlzYWJsaXR5JTIwYWlkJTIwc29sdXRpb25zfGVufDB8fDB8fHww',
    link: 'disabilityaidsolutions.com.au',
  },
  {
    title: 'Cedrus Africa Group',
    description:
      'A corporate website built to showcase the services and expertise of Cedrus Africa Group, a leading provider of business solutions across various industries.',
    tags: ['Wordpress'],
    image:
      'https://images.unsplash.com/photo-1626695436783-d942d5928174?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTB8fGJhbmtpbmclMjBhZnJpY2F8ZW58MHx8MHx8fDA%3D',
    link: 'http://kenswealth.storehive.com.ng/',
  },
  {
    title: 'Dre hotels',
    description:
      'Dre Hotels is a modern, responsive hotel booking web application built to explore popular, top-rated, and upcoming hotels.',
    tags: ['Vue.js', 'API', 'Tailwind CSS'],
    image:
      'https://images.unsplash.com/photo-1551882547-ff40c63fe5fa?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8aG90ZWxzfGVufDB8fDB8fHww',
    link: 'https://dre-hotel.vercel.app/',
  },
])

const experience = ref([
  {
    company: 'Korrex Designs',
    role: 'Graphic Designer',
    period: '2019 - 2021',
    description:
      'Started as a graphic designer, creating visual content for clients across various industries',
  },
  {
    company: 'Golden Edge Softech',
    role: 'Junior Frontend Developer',
    period: '2022 - Present',
    description:
      'Leading Vue.js projects learning from great minds, building websites and software solutions',
  },
])

const activeSection = ref('home')

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
    activeSection.value = sectionId
  }
}

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          activeSection.value = entry.target.id
        }
      })
    },
    { threshold: 0.5 },
  )

  sections.value.forEach((section) => {
    const element = document.getElementById(section.id)
    if (element) observer.observe(element)
  })
})
</script>

<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-900 via-black to-gray-900 text-white">
    <!-- Navigation -->
    <nav class="fixed w-full z-50 bg-black/80 backdrop-blur-lg border-b border-gray-800">
      <div class="container mx-auto px-6 py-4">
        <div class="flex justify-between items-center">
          <div class="flex items-center space-x-2">
            <img src="/ZBR5I-removebg-preview.png" alt="Logo" class="w-14 h-16" />
          </div>

          <div class="hidden md:flex space-x-8">
            <button
              v-for="section in sections"
              :key="section.id"
              @click="scrollToSection(section.id)"
              :class="[
                'px-4 py-2 rounded-lg transition-all duration-300',
                activeSection === section.id
                  ? 'bg-gradient-to-r from-cyan-500/20 to-blue-500/20 text-cyan-300 border border-cyan-500/30'
                  : 'hover:bg-gray-800/50 hover:text-cyan-300',
              ]"
            >
              {{ section.label }}
            </button>
          </div>

          <button
            class="px-6 py-2 bg-gradient-to-r from-cyan-500 to-blue-500 rounded-lg font-semibold hover:shadow-lg hover:shadow-cyan-500/25 transition-all duration-300"
          >
            Get In Touch
          </button>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="min-h-screen flex items-center justify-center pt-16">
      <div class="container mx-auto px-6 text-center">
        <div class="relative inline-block mb-8 group">
          <div
            class="absolute inset-0 bg-gradient-to-r from-cyan-500 via-blue-500 to-purple-500 rounded-full blur-xl opacity-20 animate-pulse"
          ></div>
          <div
            class="absolute -inset-4 bg-gradient-to-r from-cyan-500/30 to-blue-500/30 rounded-full blur-lg opacity-10"
          ></div>

          <div
            class="relative backdrop-blur-sm bg-gradient-to-br from-white/5 to-black/20 p-2 rounded-full border border-white/10 shadow-2xl"
          >
            <div class="w-48 h-48 rounded-full overflow-hidden relative">
              <img
                src="/profile.png"
                alt="Profile"
                class="w-full h-full object-cover object-center group-hover:scale-105 transition-transform duration-700"
              />

              <div
                class="absolute inset-0 bg-gradient-to-t from-gray-900/40 via-transparent to-transparent"
              ></div>
              <div
                class="absolute inset-0 bg-gradient-to-br from-cyan-500/5 via-transparent to-purple-500/5"
              ></div>

              <div class="absolute inset-0 rounded-full border border-white/5 shadow-inner"></div>
            </div>

            <div class="absolute -bottom-3 left-1/2 transform -translate-x-1/2 flex gap-1">
              <div
                class="bg-gray-900/80 backdrop-blur-sm px-3 py-1 rounded-full border border-cyan-500/30"
              >
                <span class="text-xs font-bold text-cyan-300">Vue.js</span>
              </div>
            </div>
          </div>
        </div>

        <h1 class="text-5xl md:text-7xl font-bold mb-6">
          <span
            class="bg-gradient-to-r from-cyan-400 via-blue-400 to-purple-400 bg-clip-text text-transparent"
          >
            Frontend Jnr Dev
          </span>
        </h1>

        <p class="text-xl md:text-2xl text-gray-300 mb-8 max-w-3xl mx-auto">
          I create <span class="text-cyan-300">beautiful</span>,
          <span class="text-blue-300">interactive</span>, and
          <span class="text-purple-300">performant</span> web experiences with Vue.js and Tailwind
          CSS
        </p>

        <div class="flex flex-wrap justify-center gap-6 mb-12">
          <button
            href="#projects"
            class="px-8 py-3 bg-gradient-to-r from-cyan-500 to-blue-500 rounded-full font-semibold flex items-center gap-2 hover:shadow-lg hover:shadow-cyan-500/25 transition-all duration-300"
          >
            <BriefcaseIcon class="h-5 w-5" />
            View Projects
          </button>
          <button
            class="px-8 py-3 border-2 border-cyan-500/30 rounded-full font-semibold flex items-center gap-2 hover:bg-cyan-500/10 transition-all duration-300"
          >
            <DocumentTextIcon class="h-5 w-5" />
            Download CV
          </button>
        </div>

        <div class="animate-bounce mt-20">
          <ArrowDownIcon class="h-8 w-8 mx-auto text-cyan-400" />
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="py-20">
      <div class="container mx-auto px-6">
        <div class="text-center mb-16">
          <SparklesIcon class="h-12 w-12 text-yellow-400 mx-auto mb-4" />
          <h2 class="text-4xl font-bold mb-4">Expertise & Skills</h2>
          <p class="text-gray-400 text-lg">Technologies I work with daily</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div
            v-for="skill in skills"
            :key="skill.name"
            class="bg-gradient-to-br from-gray-800/50 to-gray-900/50 p-6 rounded-2xl border border-gray-700/50 hover:border-cyan-500/30 transition-all duration-300"
          >
            <div class="flex justify-between items-center mb-4">
              <h3 class="text-xl font-semibold">{{ skill.name }}</h3>
              <span class="text-cyan-400 font-bold">{{ skill.level }}%</span>
            </div>
            <div class="h-3 bg-gray-700 rounded-full overflow-hidden">
              <div
                :class="`h-full bg-gradient-to-r ${skill.color} rounded-full transition-all duration-1000`"
                :style="{ width: skill.level + '%' }"
                ref="skillBar"
              ></div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="py-20 bg-gradient-to-b from-transparent to-gray-900/50">
      <div class="container mx-auto px-6">
        <div class="text-center mb-16">
          <CodeBracketIcon class="h-12 w-12 text-purple-400 mx-auto mb-4" />
          <h2 class="text-4xl font-bold mb-4">Featured Projects</h2>
          <p class="text-gray-400 text-lg">Showcasing my best work</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div
            v-for="project in projects"
            :key="project.title"
            class="group bg-gradient-to-br from-gray-800 to-gray-900 rounded-2xl overflow-hidden border border-gray-700/50 hover:border-cyan-500/50 transition-all duration-300 hover:scale-[1.02]"
          >
            <div class="h-48 overflow-hidden">
              <img
                :src="project.image"
                :alt="project.title"
                class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500"
              />
            </div>

            <div class="p-6">
              <h3 class="text-2xl font-bold mb-2">{{ project.title }}</h3>
              <p class="text-gray-400 mb-4">{{ project.description }}</p>

              <div class="flex flex-wrap gap-2 mb-6">
                <span
                  v-for="tag in project.tags"
                  :key="tag"
                  class="px-3 py-1 bg-cyan-500/10 text-cyan-300 rounded-full text-sm"
                >
                  {{ tag }}
                </span>
              </div>

              <a
                :href="project.link"
                target="_blank"
                class="inline-flex items-center justify-center gap-2 rounded-full px-5 py-3 bg-cyan-500/10 text-cyan-200 font-semibold border border-cyan-500/30 shadow-sm shadow-cyan-500/10 transition-all duration-300 hover:bg-cyan-500/20 hover:text-white hover:shadow-cyan-500/30"
              >
                View Project
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Experience Section -->
    <section id="experience" class="py-20">
      <div class="container mx-auto px-6">
        <div class="text-center mb-16">
          <AcademicCapIcon class="h-12 w-12 text-green-400 mx-auto mb-4" />
          <h2 class="text-4xl font-bold mb-4">Experience</h2>
          <p class="text-gray-400 text-lg">My professional journey</p>
        </div>

        <div class="max-w-3xl mx-auto">
          <div class="relative">
            <!-- Timeline line -->
            <div
              class="absolute left-8 md:left-1/2 transform md:-translate-x-px h-full w-0.5 bg-gradient-to-b from-cyan-500 via-blue-500 to-purple-500"
            ></div>

            <!-- Timeline items -->
            <div
              v-for="(exp, index) in experience"
              :key="exp.company"
              :class="[
                'relative mb-12',
                index % 2 === 0
                  ? 'md:mr-auto md:pr-16 md:pl-0 md:text-right'
                  : 'md:ml-auto md:pl-16',
              ]"
            >
              <div class="flex items-center md:block">
                <!-- Timeline dot -->
                <div
                  class="absolute left-6 md:left-1/2 transform md:-translate-x-1/2 w-4 h-4 bg-gradient-to-r from-cyan-500 to-blue-500 rounded-full border-4 border-gray-900 z-10"
                ></div>

                <!-- Content -->
                <div :class="['ml-16 md:ml-0', index % 2 === 0 ? 'md:mr-8' : 'md:ml-8']">
                  <div
                    class="bg-gradient-to-br from-gray-800 to-gray-900 p-6 rounded-2xl border border-gray-700/50"
                  >
                    <h3 class="text-xl font-bold mb-2">{{ exp.role }}</h3>
                    <h4 class="text-cyan-400 font-semibold mb-2">{{ exp.company }}</h4>
                    <p class="text-gray-400 mb-3">{{ exp.period }}</p>
                    <p class="text-gray-300">{{ exp.description }}</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-20 bg-gradient-to-b from-transparent to-black">
      <div class="container mx-auto px-6">
        <div class="text-center mb-16">
          <ChatBubbleLeftRightIcon class="h-12 w-12 text-pink-400 mx-auto mb-4" />
          <h2 class="text-4xl font-bold mb-4">Let's Work Together</h2>
          <p class="text-gray-400 text-lg">Have a project in mind? I'd love to hear about it</p>
        </div>

        <div class="max-w-2xl mx-auto">
          <div
            class="bg-gradient-to-br from-gray-800/50 to-gray-900/50 p-8 rounded-2xl border border-gray-700/50"
          >
            <!-- 1. Sign up at Formspree.io to get your unique ID -->
            <form action="https://formspree.io/f/mkoyzwog" method="POST" class="space-y-6">
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                  <label class="block text-sm font-medium text-gray-300 mb-2">Name</label>
                  <input
                    type="text"
                    name="name"
                    required
                    class="w-full px-4 py-3 bg-gray-900/50 border border-gray-700 rounded-lg focus:outline-none focus:border-cyan-500 transition-colors"
                    placeholder="Your name"
                  />
                </div>
                <div>
                  <label class="block text-sm font-medium text-gray-300 mb-2">Email</label>
                  <input
                    type="email"
                    name="email"
                    required
                    class="w-full px-4 py-3 bg-gray-900/50 border border-gray-700 rounded-lg focus:outline-none focus:border-cyan-500 transition-colors"
                    placeholder="your@email.com"
                  />
                </div>
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-300 mb-2">Message</label>
                <textarea
                  name="message"
                  rows="4"
                  required
                  class="w-full px-4 py-3 bg-gray-900/50 border border-gray-700 rounded-lg focus:outline-none focus:border-cyan-500 transition-colors resize-none"
                  placeholder="Tell me about your project..."
                ></textarea>
              </div>

              <button
                type="submit"
                class="w-full py-4 bg-gradient-to-r from-cyan-500 to-blue-500 rounded-lg font-bold text-lg hover:shadow-xl hover:shadow-cyan-500/25 transition-all duration-300 flex items-center justify-center gap-2"
              >
                Send Message
              </button>
            </form>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="py-8 border-t border-gray-800">
      <div class="container mx-auto px-6">
        <div class="flex flex-col md:flex-row justify-between items-center">
          <div class="flex items-center space-x-2 mb-4 md:mb-0">
            <CodeBracketIcon class="h-6 w-6 text-cyan-400" />
            <span
              class="text-xl font-bold bg-gradient-to-r from-cyan-400 to-blue-500 bg-clip-text text-transparent"
            >
              Andre
            </span>
          </div>

          <div class="flex space-x-6">
            <a href="#" class="text-gray-400 hover:text-cyan-400 transition-colors">GitHub</a>
            <a href="#" class="text-gray-400 hover:text-blue-400 transition-colors">LinkedIn</a>
            <a href="#" class="text-gray-400 hover:text-purple-400 transition-colors">Twitter</a>
            <a href="https://wa.me/07010184699" target="_blank" rel="noopener noreferrer" class="text-gray-400 hover:text-pink-400 transition-colors" aria-label="Open WhatsApp chat">WhatsApp</a>
          </div>

          <p class="text-gray-500 text-sm mt-4 md:mt-0">© 2024 Andre. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
/* Custom animations */
@keyframes float {
  0%,
  100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-20px);
  }
}

.animate-float {
  animation: float 3s ease-in-out infinite;
}

/* Smooth scroll behavior */
html {
  scroll-behavior: smooth;
}

/* Custom scrollbar */
::-webkit-scrollbar {
  width: 10px;
}

::-webkit-scrollbar-track {
  background: #111827;
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(to bottom, #06b6d4, #3b82f6);
  border-radius: 5px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(to bottom, #0891b2, #2563eb);
}
</style>
