<script>
  import { onDestroy } from "svelte";
  import { link } from 'svelte-spa-router';
  
  // importing static media files: 
  import KunalPathak from "../assets/images/KunalPathak1.png";
  // import KunalPathak from "../assets/images/watch1.webp";

  let currentMessage = "";

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

  // Call the function to start the rotation
  startLanguageRotation(reactiveWelcome, 4000);

  // Personal Information - Replace with your actual details
  const personalInfo = {
    name: "Kunal Pathak",
    title: "Full Stack Developer",
  };
</script>

<main class="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100">
  <!-- Hero Section -->
  <section class="pt-16 px-6 pb-20">
    <div class="max-w-7xl mx-auto">
      <div class="grid lg:grid-cols-2 gap-12 items-center">
        
        <!-- Left Content Section -->
        <div class="space-y-8">
          <div class="space-y-6">
            <h1 class="text-5xl lg:text-6xl font-bold text-gray-800 leading-tight">
              {currentMessage}
            </h1>
            <h2 class="text-3xl lg:text-4xl font-medium text-gray-700">
              I'm <span class="text-indigo-600">{personalInfo.name}</span>
            </h2>
            <p class="text-xl text-gray-600 font-medium">{personalInfo.title}</p>
          </div>

          <div class="space-y-6">
            <p class="text-lg text-gray-600 leading-relaxed">
              Passionate developer with expertise in full-stack web development. 
              I love creating efficient, scalable solutions and exploring new technologies.
            </p>
            
            <div class="space-y-4">
              <h3 class="text-2xl font-semibold text-gray-800">What I Do</h3>
              <div class="grid gap-4">
                <div class="flex items-start space-x-3">
                  <div class="w-2 h-2 bg-indigo-500 rounded-full mt-2 flex-shrink-0"></div>
                  <p class="text-gray-600">Building responsive and interactive web applications</p>
                </div>
                <div class="flex items-start space-x-3">
                  <div class="w-2 h-2 bg-indigo-500 rounded-full mt-2 flex-shrink-0"></div>
                  <p class="text-gray-600">Developing scalable backend systems and APIs</p>
                </div>
                <div class="flex items-start space-x-3">
                  <div class="w-2 h-2 bg-indigo-500 rounded-full mt-2 flex-shrink-0"></div>
                  <p class="text-gray-600">Creating seamless user experiences with modern frameworks</p>
                </div>
              </div>
            </div>

            <div class="flex flex-wrap gap-4 pt-4">
              <a href="https://www.linkedin.com/in/kunal-pathak-162929237/"><button class="px-8 py-3 bg-indigo-600 text-font-medium rounded-lg hover:bg-indigo-transition-colors hover-lift">Get in touch</button></a>
              <a use:link href="/about"><button class="px-8 py-3 border-2 border-indigo-600 text-indigo-600 font-medium rounded-lg hover:bg-indigo-50 transition-colors hover-lift">View Portfolio</button></a>
              
            </div>
          </div>
        </div>

        <!-- Right Image Section -->
        <div class="lg:pl-12">
          <div class="relative">
            <!-- Image Container -->
            <div class="relative z-9 rounded-2xl overflow-hidden shadow-2xl hover-lift transition-transform duration-300">
              <!-- Replace this div with your actual image -->
              <img src={KunalPathak} alt="Kunal Pathak" class="w-full h-auto object-cover" />
            </div>

            <!-- Decorative Elements -->
            <div class="absolute -top-4 -right-4 w-24 h-24 bg-indigo-200 rounded-full opacity-60 -z-10"></div>
            <div class="absolute -bottom-6 -left-6 w-32 h-32 bg-purple-200 rounded-full opacity-40 -z-10"></div>
          </div>

          <!-- Additional Info Card -->
          <div class="mt-8 p-6 bg-white rounded-xl shadow-lg hover-lift transition-transform duration-300">
            <h4 class="text-lg font-semibold text-gray-800 mb-3">Quick Stats</h4>
            <div class="grid grid-cols-2 gap-4 text-center">
              <div>
                <p class="text-2xl font-bold text-indigo-600">2+</p>
                <p class="text-sm text-gray-600">Years Experience</p>
              </div>
              <div>
                <p class="text-2xl font-bold text-indigo-600">3+</p>
                <p class="text-sm text-gray-600">Projects Completed</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer class="bg-gray-800 text-white py-8">
    <div class="max-w-7xl mx-auto px-6">
      <div class="text-center">
        <p class="text-gray-300">&copy; 2025 {personalInfo.name}. All rights reserved.</p>
        <div class="mt-4 flex justify-center space-x-6">
          <a href="https://www.linkedin.com/in/kunal-pathak-162929237/" class="text-gray-400 hover:text-white transition-colors">LinkedIn</a>
          <a href="https://github.com/Kp270705" class="text-gray-400 hover:text-white transition-colors">GitHub</a>
          <a href="https://x.com/KunalP699" class="text-gray-400 hover:text-white transition-colors">Twitter</a>
        </div>
      </div>
    </div>
  </footer>
</main>

<style>
  /* Smooth scrolling for anchor links */
  :global(html) {
    scroll-behavior: smooth;
  }
  
  /* Custom hover effects */
  .hover-lift:hover {
    transform: translateY(-4px);
  }

  /* Animation for the rotating text */
  :global(.fade-in) {
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
</style>