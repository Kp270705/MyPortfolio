<!-- Home.svelte -->
<script>
  import { onDestroy, onMount } from "svelte";
  import { link } from 'svelte-spa-router';
  
  // importing static media files: 
  import KunalPathak from "../assets/images/KunalPathak1.png";

  let currentMessage = "";
  let isDarkTheme = false;

  const reactiveWelcome = {
    english: "Hello Friends",
    spanish: "Hola Amigos", 
    french: "Bonjour les amis",
    hindi: "नमस्ते दोस्तों"
  };

  function startLanguageRotation(welcomeObj, intervalTime = 5000) {
    const keys = Object.keys(welcomeObj);
    let index = 0;
    currentMessage = welcomeObj[keys[index]];

    const interval = setInterval(() => {
      index = (index + 1) % keys.length;
      currentMessage = welcomeObj[keys[index]];
    }, intervalTime);

    // Cleanup
    onDestroy(() => clearInterval(interval));
  }

  // Personal Information
  const personalInfo = {
    name: "Kunal Pathak",
    title: "Full Stack Developer",
  };

  // Theme management
  onMount(() => {
    // Check for saved theme preference or default to 'light' mode
    const savedTheme = localStorage.getItem('theme');
    if (savedTheme) {
      isDarkTheme = savedTheme === 'dark';
    } else if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
      isDarkTheme = true;
    }
    
    updateTheme();
  });

  function toggleTheme() {
    isDarkTheme = !isDarkTheme;
    localStorage.setItem('theme', isDarkTheme ? 'dark' : 'light');
    updateTheme();
  }

  function updateTheme() {
    if (isDarkTheme) {
      document.documentElement.classList.add('dark');
    } else {
      document.documentElement.classList.remove('dark');
    }
  }

  // Call the function to start the rotation
  startLanguageRotation(reactiveWelcome, 2000);
</script>

<main class="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100 dark:from-gray-900 dark:to-gray-800 transition-colors duration-300">

  <!-- Hero Section -->
  <section class="pt-32 px-6 pb-20">
    <div class="max-w-7xl mx-auto">
      <div class="grid lg:grid-cols-2 gap-12 items-center">
        
        <!-- Left Content Section -->
        <div class="space-y-8">
          <div class="space-y-6">
            <h1 class="text-5xl lg:text-6xl font-bold text-gray-800 dark:text-white leading-tight transition-colors fade-in">
              {currentMessage}
            </h1>
            <h2 class="text-3xl lg:text-4xl font-medium text-gray-700 dark:text-gray-300 transition-colors">
              I'm <span class="text-indigo-600 dark:text-indigo-400 bg-gradient-to-r from-indigo-600 to-purple-600 dark:from-indigo-400 dark:to-purple-400 bg-clip-text ">{personalInfo.name}</span>
            </h2>
            <p class="text-xl text-gray-600 dark:text-gray-400 font-medium transition-colors">{personalInfo.title}</p>
          </div>

          <div class="space-y-6">
            <p class="text-lg text-gray-600 dark:text-gray-400 leading-relaxed transition-colors">
              Passionate developer with expertise in full-stack web development. 
              I love creating efficient, scalable solutions and exploring new technologies.
            </p>
            
            <div class="space-y-4">
              <h3 class="text-2xl font-semibold text-gray-800 dark:text-white transition-colors">What I Do</h3>
              <div class="grid gap-4">
                <div class="flex items-start space-x-3 group">
                  <div class="w-2 h-2 bg-indigo-500 dark:bg-indigo-400 rounded-full mt-2 flex-shrink-0 group-hover:scale-125 transition-transform"></div>
                  <p class="text-gray-600 dark:text-gray-400 transition-colors">Building responsive and interactive web applications</p>
                </div>
                <div class="flex items-start space-x-3 group">
                  <div class="w-2 h-2 bg-indigo-500 dark:bg-indigo-400 rounded-full mt-2 flex-shrink-0 group-hover:scale-125 transition-transform"></div>
                  <p class="text-gray-600 dark:text-gray-400 transition-colors">Developing scalable backend systems and APIs</p>
                </div>
                <div class="flex items-start space-x-3 group">
                  <div class="w-2 h-2 bg-indigo-500 dark:bg-indigo-400 rounded-full mt-2 flex-shrink-0 group-hover:scale-125 transition-transform"></div>
                  <p class="text-gray-600 dark:text-gray-400 transition-colors">Creating seamless user experiences with modern frameworks</p>
                </div>
              </div>
            </div>

            <div class="flex flex-wrap gap-4 pt-4">
              <a 
                href="https://www.linkedin.com/in/kunal-pathak-162929237/"
                class="px-8 py-3 bg-gradient-to-r from-indigo-600 to-purple-600 text-white font-medium rounded-xl hover:from-indigo-700 hover:to-purple-700 transition-all duration-300 hover-lift shadow-lg hover:shadow-xl"
              >
                Get in touch
              </a>
              <a 
                use:link 
                href="/about"
                class="px-8 py-3 border-2 border-indigo-600 dark:border-indigo-400 text-indigo-600 dark:text-indigo-400 font-medium rounded-xl hover:bg-indigo-600 dark:hover:bg-indigo-400 hover:text-white transition-all duration-300 hover-lift"
              >
                View Portfolio
              </a>
            </div>
          </div>
        </div>

        <!-- Right Image Section -->
        <div class="lg:pl-12">
          <div class="relative">
            <!-- Image Container -->
            <div class="relative z-10 rounded-2xl overflow-hidden shadow-2xl hover-lift transition-all duration-300 group">
              <div class="absolute inset-0 bg-gradient-to-t from-black/20 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
              <img src={KunalPathak} alt="Kunal Pathak" class="w-full h-auto object-cover group-hover:scale-105 transition-transform duration-300" />
            </div>

            <!-- Decorative Elements -->
            <div class="absolute -top-4 -right-4 w-24 h-24 bg-gradient-to-br from-indigo-200 to-purple-200 dark:from-indigo-800 dark:to-purple-800 rounded-full opacity-60 animate-pulse"></div>
            <div class="absolute -bottom-6 -left-6 w-32 h-32 bg-gradient-to-br from-purple-200 to-pink-200 dark:from-purple-800 dark:to-pink-800 rounded-full opacity-40 animate-pulse" style="animation-delay: 1s;"></div>
          </div>

          <!-- Additional Info Card -->
          <div class="mt-8 p-6 bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm rounded-xl shadow-lg hover-lift transition-all duration-300 border border-gray-200/50 dark:border-gray-700/50">
            <h4 class="text-lg font-semibold text-gray-800 dark:text-white mb-3 transition-colors">Quick Stats</h4>
            <div class="grid grid-cols-2 gap-4 text-center">
              <div class="group">
                <p class="text-2xl font-bold bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent group-hover:scale-110 transition-transform">2+</p>
                <p class="text-sm text-gray-600 dark:text-gray-400 transition-colors">Years Experience</p>
              </div>
              <div class="group">
                <p class="text-2xl font-bold bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent group-hover:scale-110 transition-transform">3+</p>
                <p class="text-sm text-gray-600 dark:text-gray-400 transition-colors">Projects Completed</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Skills Showcase -->
  <section class="py-20 px-6 bg-white/50 dark:bg-gray-900/50 backdrop-blur-sm">
    <div class="max-w-7xl mx-auto">
      <h2 class="text-3xl font-bold text-center text-gray-800 dark:text-white mb-12 transition-colors">Technologies I Work With</h2>
      <div class="flex flex-wrap justify-center gap-4">
        {#each ["Python", "Flask", "FastAPI", "JavaScript", "Svelte", "JWT", "OAuth", "Git", "Google Cloud"] as skill}
          <span class="px-4 py-2 bg-white dark:bg-gray-800 text-gray-700 dark:text-gray-300 rounded-full shadow-sm border border-gray-200 dark:border-gray-700 hover:shadow-md hover:scale-105 transition-all duration-300">
            {skill}
          </span>
        {/each}
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer class="bg-white/80 dark:bg-black text-gray-100 py-12 transition-colors duration-300">
    <div class="max-w-7xl mx-auto px-6">
      <div class="text-center">
        <p class="text-gray-900 dark:text-gray-400 transition-colors">&copy; 2025 {personalInfo.name}. All rights reserved.</p>
        <div class="mt-6 flex justify-center space-x-6">
          <a 
            href="https://www.linkedin.com/in/kunal-pathak-162929237/" 
            class="text-gray-400 hover:text-indigo-400 transition-colors duration-300 hover:scale-110 transform"
            aria-label="LinkedIn"
          >
            <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
              <path d="M16.338 16.338H13.67V12.16c0-.995-.017-2.277-1.387-2.277-1.39 0-1.601 1.086-1.601 2.207v4.248H8.014v-8.59h2.559v1.174h.037c.356-.675 1.227-1.387 2.526-1.387 2.703 0 3.203 1.778 3.203 4.092v4.711zM5.005 6.575a1.548 1.548 0 11-.003-3.096 1.548 1.548 0 01.003 3.096zm-1.337 9.763H6.34v-8.59H3.667v8.59zM17.668 1H2.328C1.595 1 1 1.581 1 2.298v15.403C1 18.418 1.595 19 2.328 19h15.34c.734 0 1.332-.582 1.332-1.299V2.298C19 1.581 18.402 1 17.668 1z"/>
            </svg>
          </a>
          <a 
            href="https://github.com/Kp270705" 
            class="text-gray-400 hover:text-indigo-400 transition-colors duration-300 hover:scale-110 transform"
            aria-label="GitHub"
          >
            <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
              <path fill-rule="evenodd" d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .839-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.203 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.942.359.31.678.921.678 1.856 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z" clip-rule="evenodd" />
            </svg>
          </a>
          <a 
            href="https://x.com/KunalP699" 
            class="text-gray-400 hover:text-indigo-400 transition-colors duration-300 hover:scale-110 transform"
            aria-label="Twitter"
          >
            <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
              <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
            </svg>
          </a>
        </div>
      </div>
    </div>
  </footer>
</main>

<style>
  :global(html) {
    scroll-behavior: smooth;
  }
  
  :global(.dark) {
    color-scheme: dark;
  }

  .hover-lift:hover {
    transform: translateY(-4px);
  }

  .fade-in {
    animation: fadeIn 0.5s ease-in-out;
  }

  @keyframes fadeIn {
    from {
      opacity: 0;
      transform: translateY(10px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  :global(.animate-pulse) {
    animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
  }

  @keyframes pulse {
    0%, 100% {
      opacity: 0.4;
    }
    50% {
      opacity: 0.8;
    }
  }
</style>