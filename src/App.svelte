
<script>
  import Carousel from 'svelte-carousel'
  import ImageLink from './lib/ImageLink.svelte'

  // Mobile menu toggle
  let isMenuOpen = false;

  const toggleMenu = () => {
    isMenuOpen = !isMenuOpen;
  };

  const images = [
    { link: 'Portsmouth-Spinnaker.jpg', text: 'Portsmouth-Spinnaker' },
    { link: 'IMG_5934-e1479902141638.jpg', text: "Fuller's bridge" },
    { link: 'southsea-3851740_1920.jpg', text: 'South sea' },
    ]
</script>

<main class="flex flex-col min-h-screen">
  <!-- Navigation Bar -->
  <header class="bg-gray-800 text-white">
    <div class="container mx-auto px-6 py-4 flex items-center justify-between">
      <!-- Logo -->
      <a href="#" class="flex items-center gap-2 text-2xl font-bold">
        <img src="macrovision-logo.png" alt="Macrovision Property Logo" class="h-5">
        MACROVISON PROPERTY
      </a>

      <!-- Navigation Links (hidden on small screens) -->
      <nav class="hidden md:flex space-x-6">
        <a href="#home" class="hover:text-blue-400">Home</a>
        <a href="#properties" class="hover:text-blue-400">Properties</a>
        <a href="#about" class="hover:text-blue-400">About</a>
        <a href="#contact" class="hover:text-blue-400">Contact</a>
      </nav>

      <!-- Hamburger Menu (visible on small screens) -->
      <button 
        on:click={toggleMenu} 
        class="md:hidden focus:outline-none"
        aria-label="Toggle menu">
        <svg class="w-6 h-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
      </button>
    </div>

    <!-- Mobile Menu -->
    <div class={`md:hidden bg-gray-700 ${isMenuOpen ? '' : 'hidden'}`}>
      <a href="#home" class="block px-4 py-2 hover:bg-gray-600">Home</a>
      <a href="#properties" class="block px-4 py-2 hover:bg-gray-600">Properties</a>
      <a href="#about" class="block px-4 py-2 hover:bg-gray-600">About</a>
      <a href="#contact" class="block px-4 py-2 hover:bg-gray-600">Contact</a>
    </div>
  </header>

  <!-- Carousel Section -->
  <section id="carousel" class="relative w-full bg-gray-100">
    <Carousel>
    {#each images as { link, text } }
      <ImageLink {link} {text} />
    {/each}
    </Carousel>
  </section>

  <!-- Footer -->
  <footer class="bg-gray-800 text-white mt-auto">
    <div class="container mx-auto px-6 py-8 grid grid-cols-1 md:grid-cols-3 gap-6">
      <!-- About Section -->
      <div id="about">
        <h3 class="text-xl font-bold mb-2">About Us</h3>
        <p class="text-sm text-gray-400">We help you find the home of your dreams with the best listings available.</p>
      </div>
      <!-- Quick Links -->
      <div>
        <h3 class="text-xl font-bold mb-2">Quick Links</h3>
        <ul class="space-y-2">
          <li><a href="#home" class="hover:text-blue-400">Home</a></li>
          <li><a href="#properties" class="hover:text-blue-400">Properties</a></li>
          <li><a href="#about" class="hover:text-blue-400">About</a></li>
          <li><a href="#contact" class="hover:text-blue-400">Contact</a></li>
        </ul>
      </div>
      <!-- Contact Section -->
      <div id="contact">
        <h3 class="text-xl font-bold mb-2">Contact Us</h3>
        <p class="text-sm text-gray-400">
          Email:
          <a href="mailto:info@macrovisionproperty.com" aria-label="email us at info@macrovisionproperty.com" target="_blank">
            info@macrovisionproperty.com
          </a>
        </p>
        <p class="text-sm text-gray-400">
          Phone:
            <a href="tel:+254795360285" aria-label="call us at +254795360285" target="_blank">
              +254 795 360285
            </a>
          </p>
      </div>
    </div>
    <div class="text-center text-gray-500 text-sm py-4 border-t border-gray-700">
      © 2025 MACROVISON PROPERTY. All rights reserved.
    </div>
  </footer>
</main>
