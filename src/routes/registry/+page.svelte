<script lang="ts">
  import { onMount } from 'svelte';
  import { goto } from "$app/navigation";


  type FloatingIcon = {
      icon: string;
      top: string;
      left: string;
      delay: number;
      id: string;
    };

  const floatingIcons: FloatingIcon[] = [
    { icon: '💍', top: '20%', left: '80%', delay: 0, id: 'heart' },
    { icon: '💍', top: '70%', left: '15%', delay: 2000, id: 'gift' },
    { icon: '✨', top: '40%', left: '10%', delay: 2000, id: 'ring1' },
    { icon: '✨', top: '40%', left: '90%', delay: 4000, id: 'sparkle1' },
    { icon: '✨', top: '80%', left: '70%', delay: 6000, id: 'sparkle2' },
    { icon: '✨', top: '10%', left: '20%', delay: 1000, id: 'sparkle3' },
    { icon: '💍', top: '60%', left: '85%', delay: 3000, id: 'ring' }
  ];

  let mounted = false;

  onMount(() => {
    mounted = true;
  });

  async function stripe_redirection() {
    window.open('https://buy.stripe.com/test_00w9AM0kuf8K4n05mCdMI00', '_blank')
    goto('/home')
  }
</script>

{#if mounted}
<div class="absolute inset-0 pointer-events-none overflow-hidden">
  {#each floatingIcons as { icon, top, left, delay, id } (id)}
    <div 
      class="absolute text-white/60 text-3xl sm:text-4xl md:text-5xl lg:text-6xl animate-float-fade"
      style="top: {top}; left: {left}; animation-delay: {delay}ms;"
    >
      {icon}
    </div>
  {/each}
</div>
{/if}

<div class="min-h-screen w-full flex flex-col justify-center items-center bg-gradient-to-br from-dark-red/70 to-dark-red/80 px-4 py-8">
  <h1 class="text-4xl sm:text-6xl md:text-7xl lg:text-8xl text-light-yellow text-center mb-6 sm:mb-8">Registry</h1>
  
  <p class="mt-4 sm:mt-10 w-full max-w-xs sm:max-w-sm md:max-w-md lg:max-w-lg xl:max-w-xl text-sm sm:text-base md:text-lg lg:text-xl text-center text-light-yellow font-light mb-6 sm:mb-8 leading-relaxed">
    We've got the dishes, the pots, and the pans,<br>
    What we'd love most is a gift to our plans!<br>
    Instead of presents wrapped up so sweet,<br>
    A gift of cash would be a special treat.
  </p>

  <div class="flex justify-center mt-6 sm:mt-10">
    <button 
      onclick={stripe_redirection} 
      class="bg-custom-white/70 text-dark-red px-6 py-3 sm:px-8 sm:py-4 text-base sm:text-lg rounded-full font-semibold transition-all duration-200 transform hover:scale-105 active:scale-95 shadow-lg border-2 border-light-yellow/5 hover:border-custom-white touch-manipulation"
    >
      RSVP Now
    </button>
  </div>
</div>

<style>
@keyframes float-fade {
    0% {
      opacity: 0;
      transform: translateY(0px) scale(0.8);
    }
    20% {
      opacity: 0.8;
      transform: translateY(-20px) scale(1);
    }
    80% {
      opacity: 0.8;
      transform: translateY(-40px) scale(1);
    }
    100% {
      opacity: 0;
      transform: translateY(-60px) scale(0.8);
    }
  }

  .animate-float-fade {
    animation: float-fade 8s ease-in-out infinite;
  }


  button {
    min-height: 44px;
  }

  @media (max-width: 640px) {
    .animate-float-fade {
      animation: float-fade 10s ease-in-out infinite;
    }
  }
</style>