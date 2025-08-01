<script>
  import { onDestroy } from "svelte";


  // Personal Information - Replace with your actual details
  const personalInfo = {
    name: "Kunal Pathak",
    title: "Full Stack Developer",
    location: "Tanakpur, Uttarakhand, India",
    email: "kunalpathak4774@gmail.com",
    phone: "+91 8979963277"
  };

  const skills = [
    "JavaScript", "Python", "Flask", "Svelte", "React", "Node.js",
    "JWT Authentication", "OAuth", "Git", "Docker", "PostgreSQL", "MongoDB"
  ];

  const projects = [
    {
      name: "Certificate Generator",
      description: "A web application for generating digital certificates using Flask backend and Svelte frontend. Features template customization and batch processing.",
      technologies: ["Flask", "Svelte", "Python", "JavaScript"],
      status: "Completed"
    },
    {
      name: "OAuth Login System",
      description: "A secure authentication system implementing OAuth 2.0 with JWT tokens for authorization. Built with Flask and includes session management.",
      technologies: ["Flask", "OAuth 2.0", "JWT", "Python", "SQLAlchemy"],
      status: "Completed"
    }
  ];

  const socialLinks = [
    {
      name: "GitHub",
      url: "https://github.com/Kp270705",
      icon: "github"
    },
    {
      name: "LinkedIn",
      url: "https://www.linkedin.com/in/kunal-pathak-162929237/",
      icon: "linkedin"
    },
    {
      name: "Reddit",
      url: "https://www.reddit.com/user/Sudden_Complaint_837/",
      icon: "reddit"
    }
  ];
</script>

<main class="min-h-screen bg-gray-50">

  <!-- About Section -->
  <section id="about" class="py-12 px-6 bg-white">
    <div class="max-w-4xl mx-auto">
      <h2 class="text-3xl font-bold text-gray-800 mb-8 text-center">About Me</h2>
      <div class="grid md:grid-cols-2 gap-8 items-center">
        <div>
          <p class="text-gray-600 leading-relaxed mb-4">
            I'm a dedicated full-stack developer with a passion for creating innovative web solutions. 
            My journey in software development has led me to specialize in modern web technologies 
            and secure authentication systems.
          </p>
          <p class="text-gray-600 leading-relaxed">
            I enjoy working on projects that challenge me to learn new technologies and solve 
            complex problems. When I'm not coding, you can find me exploring the latest tech trends 
            or contributing to open-source projects.
          </p>
        </div>
        <div class="space-y-3">
          <div class="flex items-center space-x-3">
            <svg class="w-5 h-5 text-gray-400" fill="currentColor" viewBox="0 0 20 20">
              <path fill-rule="evenodd" d="M5.05 4.05a7 7 0 119.9 9.9L10 18.9l-4.95-4.95a7 7 0 010-9.9zM10 11a2 2 0 100-4 2 2 0 000 4z" clip-rule="evenodd" />
            </svg>
            <span class="text-gray-600">{personalInfo.location}</span>
          </div>
          <div class="flex items-center space-x-3">
            <svg class="w-5 h-5 text-gray-400" fill="currentColor" viewBox="0 0 20 20">
              <path d="M2.003 5.884L10 9.882l7.997-3.998A2 2 0 0016 4H4a2 2 0 00-1.997 1.884z" />
              <path d="M18 8.118l-8 4-8-4V14a2 2 0 002 2h12a2 2 0 002-2V8.118z" />
            </svg>
            <a href="mailto:{personalInfo.email}" class="text-gray-600 hover:text-blue-600 transition-colors">
              {personalInfo.email}
            </a>
          </div>
          <div class="flex items-center space-x-3">
            <svg class="w-5 h-5 text-gray-400" fill="currentColor" viewBox="0 0 20 20">
              <path d="M2 3a1 1 0 011-1h2.153a1 1 0 01.986.836l.74 4.435a1 1 0 01-.54 1.06l-1.548.773a11.037 11.037 0 006.105 6.105l.774-1.548a1 1 0 011.059-.54l4.435.74a1 1 0 01.836.986V17a1 1 0 01-1 1h-2C7.82 18 2 12.18 2 5V3z" />
            </svg>
            <span class="text-gray-600">{personalInfo.phone}</span>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Skills Section -->
  <section id="skills" class="py-12 px-6">
    <div class="max-w-4xl mx-auto">
      <h2 class="text-3xl font-bold text-gray-800 mb-8 text-center">Skills</h2>
      <div class="flex flex-wrap justify-center gap-3">
        {#each skills as skill}
          <span class="px-4 py-2 bg-white text-gray-700 rounded-full shadow-sm border border-gray-200 hover:shadow-md transition-shadow">
            {skill}
          </span>
        {/each}
      </div>
    </div>
  </section>

  <!-- Projects Section -->
  <section id="projects" class="py-12 px-6 bg-white">
    <div class="max-w-4xl mx-auto">
      <h2 class="text-3xl font-bold text-gray-800 mb-8 text-center">Projects</h2>
      <div class="grid md:grid-cols-2 gap-6">
        {#each projects as project}
          <div class="bg-gray-50 p-6 rounded-lg border border-gray-200 hover:shadow-md transition-shadow">
            <div class="flex justify-between items-start mb-3">
              <h3 class="text-xl font-semibold text-gray-800">{project.name}</h3>
              <span class="px-2 py-1 text-xs bg-green-100 text-green-800 rounded-full">
                {project.status}
              </span>
            </div>
            <p class="text-gray-600 mb-4 leading-relaxed">{project.description}</p>
            <div class="flex flex-wrap gap-2">
              {#each project.technologies as tech}
                <span class="px-2 py-1 text-xs bg-blue-100 text-blue-800 rounded">
                  {tech}
                </span>
              {/each}
            </div>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <!-- Social Links Section -->
  <section class="py-12 px-6">
    <div class="max-w-4xl mx-auto text-center">
      <h2 class="text-3xl font-bold text-gray-800 mb-8">Let's Connect</h2>
      <div class="flex justify-center space-x-6">
        {#each socialLinks as link}
          <a 
            href={link.url} 
            target="_blank" 
            rel="noopener noreferrer"
            class="flex items-center space-x-2 px-4 py-2 bg-white text-gray-700 rounded-lg shadow-sm border border-gray-200 hover:shadow-md hover:text-blue-600 transition-all"
          >
            {#if link.icon === 'github'}
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
                <path fill-rule="evenodd" d="M10 0C4.477 0 0 4.484 0 10.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .839-.27 2.75 1.026A9.564 9.564 0 0110 4.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.203 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.942.359.31.678.921.678 1.856 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0020 10.017C20 4.484 15.522 0 10 0z" clip-rule="evenodd" />
              </svg>
            {:else if link.icon === 'linkedin'}
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
                <path d="M16.338 16.338H13.67V12.16c0-.995-.017-2.277-1.387-2.277-1.39 0-1.601 1.086-1.601 2.207v4.248H8.014v-8.59h2.559v1.174h.037c.356-.675 1.227-1.387 2.526-1.387 2.703 0 3.203 1.778 3.203 4.092v4.711zM5.005 6.575a1.548 1.548 0 11-.003-3.096 1.548 1.548 0 01.003 3.096zm-1.337 9.763H6.34v-8.59H3.667v8.59zM17.668 1H2.328C1.595 1 1 1.581 1 2.298v15.403C1 18.418 1.595 19 2.328 19h15.34c.734 0 1.332-.582 1.332-1.299V2.298C19 1.581 18.402 1 17.668 1z"/>
              </svg>
            {:else if link.icon === 'reddit'}
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
                <path d="M16.5 10.5c0-.883-.718-1.6-1.6-1.6-.425 0-.816.17-1.097.445-1.084-.695-2.514-1.133-4.096-1.194l.847-3.96 2.668.593c.066.757.693 1.365 1.483 1.365.828 0 1.5-.672 1.5-1.5s-.672-1.5-1.5-1.5c-.618 0-1.146.375-1.38.908L10.29 3.61c-.04-.016-.085-.016-.128-.016-.04 0-.082.016-.118.032l-.934 4.382c-1.582.06-3.012.499-4.096 1.194-.281-.275-.672-.445-1.097-.445-.882 0-1.6.717-1.6 1.6 0 .638.375 1.186.914 1.448-.016.125-.025.253-.025.382 0 1.948 2.268 3.527 5.067 3.527 2.8 0 5.067-1.579 5.067-3.527 0-.129-.009-.257-.025-.382.539-.262.914-.81.914-1.448zm-5.5.5c.552 0 1 .448 1 1s-.448 1-1 1-1-.448-1-1 .448-1 1-1zm-2.274 2.274c.178-.178.467-.178.645 0 .178.178.178.467 0 .645L8.726 14.5c-.089.089-.206.134-.323.134s-.234-.045-.323-.134c-.178-.178-.178-.467 0-.645l.646-.781zm3.548 0L13.5 14.5c-.089.089-.206.134-.323.134s-.234-.045-.323-.134c-.178-.178-.178-.467 0-.645.178-.178.467-.178.645 0 .178.178.178.467 0 .645z"/>
              </svg>
            {/if}
            <span>{link.name}</span>
          </a>
        {/each}
      </div>
    </div>
  </section>

  <!-- Contact Section -->
  <section id="contact" class="py-12 px-6 bg-white">
    <div class="max-w-4xl mx-auto text-center">
      <h2 class="text-3xl font-bold text-gray-800 mb-8">Get In Touch</h2>
      <p class="text-gray-600 mb-6 max-w-2xl mx-auto">
        I'm always interested in new opportunities and collaborations. 
        Feel free to reach out if you'd like to work together or just want to say hello!
      </p>
      <a 
        href="mailto:{personalInfo.email}" 
        class="inline-block px-6 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors"
      >
        Send Me an Email
      </a>
    </div>
  </section>

  <!-- Footer -->
  <footer class="py-6 px-6 bg-gray-800 text-white text-center">
    <p>&copy; 2025 {personalInfo.name}. All rights reserved.</p>
  </footer>
</main>

<style>
  /* Smooth scrolling for anchor links */
  :global(html) {
    scroll-behavior: smooth;
  }
  
  /* Custom hover effects */
  .hover-lift:hover {
    transform: translateY(-2px);
  }
</style>