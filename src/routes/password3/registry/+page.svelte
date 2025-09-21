<script lang="ts">
  import { onMount } from 'svelte';
  import { goto } from "$app/navigation";

  async function stripe_redirection_honeymoon() {
    window.open('https://buy.stripe.com/bJe4gB7TO3Om12f3DT5kk01', '_blank')
  }

  async function stripe_redirection_apartment() {
    window.open('https://buy.stripe.com/8x29AVca498G4er5M15kk00', '_blank')
  }

  async function go_home(){
    goto('/password3/home')
  }
</script>



<div class="min-h-screen w-full flex flex-col justify-center items-center bg-bg-white px-4 py-8">

  <img src="/flower_reg.svg" 
  class="absolute left-2 hidden sm:block md:left-6 lg:left-8 top-1/2 -translate-y-1/2 w-48 h-48 sm:w-56 sm:h-56 md:w-64 md:h-64 lg:w-80 lg:h-80 xl:w-96 xl:h-96 opacity-40 sm:opacity-45 md:opacity-50" 
  alt="Floral decoration" />
  <img src="/flower_reg.svg" 
  class="absolute left-2 hidden sm:block md:left-6 lg:left-8 top-1/2 -translate-y-1/2 w-48 h-48 sm:w-56 sm:h-56 md:w-64 md:h-64 lg:w-80 lg:h-80 xl:w-96 xl:h-96 opacity-40 sm:opacity-45 md:opacity-50" 
  alt="Floral decoration" />

<!-- Right side floral (flipped) -->
  <img src="/flower_reg.svg" 
    class="absolute right-2 hidden sm:block md:right-6 lg:right-8 top-1/2 -translate-y-1/2 w-48 h-48 sm:w-56 sm:h-56 md:w-64 md:h-64 lg:w-80 lg:h-80 xl:w-96 xl:h-96 opacity-40 sm:opacity-45 md:opacity-50 scale-x-[-1]" 
    alt="Floral decoration" />
  <img src="/flower_reg.svg" 
    class="absolute right-2 hidden sm:block md:right-6 lg:right-8 top-1/2 -translate-y-1/2 w-48 h-48 sm:w-56 sm:h-56 md:w-64 md:h-64 lg:w-80 lg:h-80 xl:w-96 xl:h-96 opacity-40 sm:opacity-45 md:opacity-50 scale-x-[-1]" 
    alt="Floral decoration" />

  <h1 class="text-4xl sm:text-6xl md:text-7xl lg:text-8xl text-primary-text font-script text-center mb-6 sm:mb-8">Registry</h1>
  
  <p class="mt-4 sm:mt-10 w-full max-w-xs sm:max-w-sm md:max-w-md lg:max-w-lg xl:max-w-xl text-sm sm:text-base md:text-lg lg:text-xl text-center text-secondary-text font-light mb-6 sm:mb-8 leading-relaxed">
    We've got the dishes, the pots, and the pans,<br>
    What we'd love most is a gift to our plans!<br>
    Instead of presents wrapped up so sweet,<br>
    A gift of cash would be a special treat.
  </p>

  <h2 class="mt-4 sm:mt-10 w-full max-w-xs sm:max-w-sm md:max-w-md lg:max-w-lg xl:max-w-xl text-sm sm:text-base md:text-lg lg:text-xl text-center text-secondary-text  leading-relaxed">
    Help Fund Our Honeymoon!
  </h2>

  <div class="flex justify-center mt-3 sm:mt-5">
    <button 
      onclick={stripe_redirection_honeymoon} 
      class="bg-secondary-text/65 hover:bg-primary-text/50 text-custom-yellow px-8 py-3 rounded-full font-semibold transition-all duration-200 transform hover:scale-105 shadow-lg border-2 border-dark-red/5 hover:border-primary-text/5 hover:text-secondary-text/70">
      Honeymoon Fund
    </button>
  </div>

  <h2 class="mt-5 sm:mt-10 w-full max-w-xs sm:max-w-sm md:max-w-md lg:max-w-lg xl:max-w-xl text-sm sm:text-base md:text-lg lg:text-xl text-center text-secondary-text leading-relaxed">
    Help Fund Our Apartment!
  </h2>

  <div class="flex justify-center mt-3 sm:mt-5">
    <button 
      onclick={stripe_redirection_apartment} 
      class="bg-secondary-text/65 hover:bg-primary-text/50 text-custom-yellow px-8 py-3 rounded-full font-semibold transition-all duration-200 transform hover:scale-105 shadow-lg border-2 border-dark-red/5 hover:border-primary-text/5 hover:text-secondary-text/70">
      Apartment Fund
    </button>
  </div>

  <div class="w-16 sm:w-24 md:w-32 lg:w-40 xl:w-48 h-0.5 bg-secondary-text/50 mx-auto mt-6"></div>

  <div class="flex justify-center mt-3 sm:mt-5">
    <button 
      onclick={go_home} 
      class="border-2 border-primary-text/8 text-secondary-text/70 bg-primary-text/60 hover:bg-secondary-text/70 hover:text-custom-yellow px-8 py-3 rounded-full font-semibold transition-all duration-200 transform hover:scale-105 shadow-lg">
      Home
    </button>
  </div>
</div>
