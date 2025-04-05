<template>
  <div class="min-h-screen p-4 md:p-8">
    <!-- Dark Mode Toggle -->
    <button @click="toggleDarkMode" 
            class="fixed top-4 right-4 w-10 h-10 rounded-full bg-gray-200 dark:bg-gray-700 hover:bg-gray-300 dark:hover:bg-gray-600 hover:scale-110 flex items-center justify-center transition-all">
      <Icon v-if="isDarkMode" name="ph:sun-bold" class="w-5 h-5" />
      <Icon v-else name="ph:moon-bold" class="w-5 h-5" />
    </button>

    <!-- CV Container -->
    <div class="max-w-cv mx-auto bg-white dark:bg-gray-800 shadow-xl rounded-xl overflow-hidden">
      <!-- Header Section -->
      <header class="relative bg-gradient-to-br from-blue-600 to-blue-400 text-gray-50 p-8 md:p-12 rounded-t-xl overflow-hidden">
        <div 
          class="absolute inset-0 opacity-5 blur-xl bg-cover bg-center transition-all duration-300"
          :style="{ backgroundImage: `url('${avatar || defaultAvatarUrl}')` }"
        ></div>
        <div class="relative">
          <div class="grid md:grid-cols-[200px_1fr] gap-8 items-center">
            <!-- Avatar Section -->
            <div class="animate-fadeIn flex justify-center md:justify-start">
              <AvatarUpload
                alt="Vu Duc Giang"
                v-model="avatar"
                readonly
              />
            </div>

            <!-- Info Section -->
            <div class="text-center md:text-left space-y-6 animate-slideUp">
              <div>
                <h1 class="text-4xl font-bold mb-2 text-white drop-shadow-sm">Vu Duc Giang</h1>
                <h2 class="text-2xl text-blue-50/90">Full Stack Developer</h2>
              </div>
              
              <div class="flex flex-col md:flex-row items-center gap-6">
                <a href="tel:0384043718" class="contact-item group transition-all hover:text-white">
                  <div class="flex items-center gap-2">
                    <div class="w-9 h-9 bg-white/15 rounded-full group-hover:bg-blue-400/30 transition-colors flex items-center justify-center">
                      <Icon name="ph:phone-bold" class="w-5 h-5 text-blue-50" />
                    </div>
                    <span class="text-blue-50 group-hover:text-white transition-colors">0384043718</span>
                  </div>
                </a>
                <a href="mailto:ducgiang1.nd1808@gmail.com" class="contact-item group transition-all hover:text-white">
                  <div class="flex items-center gap-2">
                    <div class="w-9 h-9 bg-white/15 rounded-full group-hover:bg-blue-400/30 transition-colors flex items-center justify-center">
                      <Icon name="ph:envelope-simple-bold" class="w-5 h-5 text-blue-50" />
                    </div>
                    <span class="text-blue-50 group-hover:text-white transition-colors">ducgiang1.nd1808@gmail.com</span>
                  </div>
                </a>
              </div>
              
              <!-- Social Links -->
              <div class="flex justify-center md:justify-start gap-4">
                <a href="https://github.com/VuDucGiang" target="_blank" 
                   class="w-9 h-9 bg-white/15 rounded-full hover:bg-blue-400/30 transition-all hover:scale-110 flex items-center justify-center">
                  <Icon name="ph:github-logo-bold" class="w-5 h-5 text-blue-50" />
                </a>
                <a href="https://www.linkedin.com/in/vu-giang-167785304" target="_blank" 
                   class="w-9 h-9 bg-white/15 rounded-full hover:bg-blue-400/30 transition-all hover:scale-110 flex items-center justify-center">
                  <Icon name="ph:linkedin-logo-bold" class="w-5 h-5 text-blue-50" />
                </a>
              </div>
            </div>
          </div>
        </div>
      </header>

      <!-- Main Content -->
      <main class="p-8">
        <!-- Summary Section -->
        <section class="mb-section">
          <h2 class="section-title">Summary</h2>
          <p class="text-gray-600 dark:text-gray-300 leading-relaxed">
            Full Stack Developer with over 3 years of experience in Front-End Web Development and C#.NET technologies. 
            Proficient in Object-Oriented Programming (OOP) and solid understanding of SOLID principles. 
            Passionate about learning new technologies and tools. 
            A proactive team player who thrives in collaborative environments and enjoys solving challenging problems.
          </p>
        </section>

        <!-- Technical Skills Section -->
        <section class="mb-section">
          <h2 class="section-title">Technical Skills</h2>
          <div class="space-y-4">
            <div>
              <h3 class="font-semibold mb-2">Languages</h3>
              <div class="flex flex-wrap gap-2">
                <span class="skill-tag">C#</span>
                <span class="skill-tag">JavaScript</span>
                <span class="skill-tag">HTML</span>
                <span class="skill-tag">CSS</span>
                <span class="skill-tag">SQL</span>
              </div>
            </div>
            <div>
              <h3 class="font-semibold mb-2">Frameworks/Platforms</h3>
              <div class="flex flex-wrap gap-2">
                <span class="skill-tag">VueJS</span>
                <span class="skill-tag">jQuery</span>
                <span class="skill-tag">Bootstrap</span>
                <span class="skill-tag">Tailwind</span>
                <span class="skill-tag">ASP.NET MVC</span>
                <span class="skill-tag">Web API</span>
              </div>
            </div>
            <div>
              <h3 class="font-semibold mb-2">Databases</h3>
              <div class="flex flex-wrap gap-2">
                <span class="skill-tag">MS SQL Server</span>
                <span class="skill-tag">MySQL</span>
                <span class="skill-tag">MongoDB</span>
              </div>
            </div>
            <div>
              <h3 class="font-semibold mb-2">Tools</h3>
              <div class="flex flex-wrap gap-2">
                <span class="skill-tag">Git</span>
                <span class="skill-tag">TFS</span>
                <span class="skill-tag">Jira</span>
              </div>
            </div>
          </div>
        </section>

        <!-- Education Section -->
        <section class="mb-section">
          <h2 class="section-title">Education</h2>
          <div class="timeline-item">
            <div class="timeline-dot"></div>
            <h3 class="font-semibold text-lg">VNU Hanoi – University of Engineering and Technology</h3>
            <p class="text-gray-600 dark:text-gray-300">Major: Information Technology</p>
            <p class="text-gray-600 dark:text-gray-300">Duration: 2019 – 2023</p>
            <p class="text-gray-600 dark:text-gray-300">Degree Classification: Distinction</p>
          </div>
        </section>

        <!-- Professional Experience Section -->
        <section>
          <h2 class="section-title">Professional Experience</h2>
          <div class="space-y-6">
            <div class="timeline-item">
              <div class="timeline-dot"></div>
              <div class="mb-4">
                <h3 class="font-semibold text-lg">Full Stack Developer</h3>
                <p class="text-gray-600 dark:text-gray-300">MISA Software | June 2022 – Present</p>
              </div>

              <div class="space-y-6">
                <!-- TaskGo Project -->
                <div>
                  <h4 class="font-semibold mb-2">Project: TaskGo</h4>
                  <ul class="list-disc list-inside space-y-2 text-gray-600 dark:text-gray-300">
                    <li>Developed and maintained web applications using C# .NET</li>
                    <li>Enhanced UI and front-end functionality with Vue.js for a seamless user experience</li>
                    <li>Collaborated with team members to clarify and refine project requirements</li>
                    <li>Designed and optimized database schemas to improve system performance</li>
                    <li>Implemented data import/export features using RabbitMQ and Socket</li>
                    <li>Debugged and optimized existing code for better performance</li>
                    <li>Authored technical documentation to support new developer onboarding</li>
                  </ul>
                </div>

                <!-- SalaGov Project -->
                <div>
                  <h4 class="font-semibold mb-2">Project: SalaGov</h4>
                  <ul class="list-disc list-inside space-y-2 text-gray-600 dark:text-gray-300">
                    <li>Built core application features with C#.NET and Vue.js</li>
                    <li>Maintained a productivity rate 1.5x higher than the team average</li>
                    <li>Developed payroll and tax calculation modules using SpreadJS</li>
                    <li>Designed database schemas for the application</li>
                  </ul>
                </div>

                <!-- Cegov Project -->
                <div>
                  <h4 class="font-semibold mb-2">Project: Cegov</h4>
                  <ul class="list-disc list-inside space-y-2 text-gray-600 dark:text-gray-300">
                    <li>Implemented new features and fixed bugs based on business requirements</li>
                    <li>Participated in unit testing, debugging, and code refactoring</li>
                    <li>Enhanced application performance and user experience</li>
                    <li>Utilized MySQL for database management and queries</li>
                  </ul>
                </div>

                <!-- Qlts Project -->
                <div>
                  <h4 class="font-semibold mb-2">Project: Qlts</h4>
                  <ul class="list-disc list-inside space-y-2 text-gray-600 dark:text-gray-300">
                    <li>Maintained and developed modules for ASP.NET MVC web applications</li>
                    <li>Designed and built RESTful APIs for integration with web and mobile platforms</li>
                    <li>Contributed to multiple modules across the system</li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </section>
      </main>
    </div>

    <!-- Download CV Button -->
    <button 
      @click="handleDownloadCV"
      class="fixed bottom-8 right-8 flex items-center gap-2 px-4 py-2 bg-blue-500 text-white rounded-lg hover:bg-blue-600 transition-all hover:scale-105 shadow-lg"
    >
      <Icon name="ph:download-bold" class="w-5 h-5" />
      <span>Download CV</span>
    </button>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import AvatarUpload from '~/components/AvatarUpload.vue'

const colorMode = useColorMode()
const isDarkMode = ref(colorMode.value === 'dark')
const avatar = ref<string | null>(null)
const defaultAvatarUrl = '/images/avatar.jpg'

const toggleDarkMode = () => {
  colorMode.preference = colorMode.preference === 'dark' ? 'light' : 'dark'
}

const handleDownloadCV = () => {
  const link = document.createElement('a')
  link.href = '/files/FullStack_Developer_VuDucGiang.pdf'
  link.download = 'FullStack_Developer_VuDucGiang.pdf'
  document.body.appendChild(link)
  link.click()
  document.body.removeChild(link)
}

onMounted(() => {
  // Load saved avatar from localStorage
  const savedAvatar = localStorage.getItem('userAvatar')
  if (savedAvatar) {
    avatar.value = savedAvatar
  }
})
</script>
