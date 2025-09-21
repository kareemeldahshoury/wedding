<script lang="ts">
  import { onMount } from 'svelte';
  import { goto } from "$app/navigation";
  

  const weddingData = {
    bride: 'Medo',
    groom: 'Rawan',
    date: '2025-11-30',
    venue: 'Minneapolis Marriot Southwest',
    location: '801 Opus Pkwy, Minnetonka, MN 55347'
  };

  let timeLeft = {
    days: 0,
    hours: 0,
    minutes: 0,
    seconds: 0
  };

  function updateCountdown() {
    const wedding = new Date(weddingData.date).getTime();
    const now = new Date().getTime();
    const distance = wedding - now;

    if (distance > 0) {
      timeLeft.days = Math.floor(distance / (1000 * 60 * 60 * 24));
      timeLeft.hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      timeLeft.minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      timeLeft.seconds = Math.floor((distance % (1000 * 60)) / 1000);
    }
  }

  onMount(() => {
    updateCountdown();
    const interval = setInterval(updateCountdown, 1000);
    return () => clearInterval(interval);
  });

  const formatDate = (dateString: string): string => {
    return new Date(dateString).toLocaleDateString('en-US', {
      weekday: 'long',
      year: 'numeric',
      month: 'long',
      day: 'numeric'
    });
  };

  async function rsvp() {
      goto("/password1/rsvp")
    }

  async function registry() {
    goto('/password1/registry')
  }


  const navItems = ['Home', 'Our Story', 'Details', 'Registry', 'RSVP'];
</script>

<div class="min-h-screen bg-bg-white">
  <section class="relative min-h-screen bg-btg-white flex items-center justify-center px-4">
    <!-- Left side floral -->
    <img src="/flower_four.svg" 
        class="absolute left-2 hidden sm:block md:left-6 lg:left-8 top-1/2 -translate-y-1/2 w-48 h-48 sm:w-56 sm:h-56 md:w-64 md:h-64 lg:w-80 lg:h-80 xl:w-96 xl:h-96 opacity-40 sm:opacity-45 md:opacity-50" 
        alt="Floral decoration" />

    <!-- Right side floral (flipped) -->
    <img src="/flower_four.svg" 
        class="absolute right-2 hidden sm:block md:right-6 lg:right-8 top-1/2 -translate-y-1/2 w-48 h-48 sm:w-56 sm:h-56 md:w-64 md:h-64 lg:w-80 lg:h-80 xl:w-96 xl:h-96 opacity-40 sm:opacity-45 md:opacity-50 scale-x-[-1]" 
        alt="Floral decoration" />

    <div class="text-center z-10 max-w-4xl mx-auto">
      <div class="mb-8">
        <h1 class="font-script text-6xl sm:text-7xl lg:text-8xl text-primary-text mb-4 ml-5 sm:ml-3 leading-tight">
          {weddingData.bride}
          <span class="text-secondary-text/80 mx-4">&</span>
          {weddingData.groom}
        </h1>
        
        <div class="w-32 h-1 bg-secondary-text/50 mx-auto mb-6"></div>
        <p class="text-3xl sm:text-5xl font-script text-secondary-text/80 font-light mb-2">
          are getting married
        </p>
        <p class="text-lg mt-3 text-secondary-text/80">
          {formatDate(weddingData.date)}
        </p>
        <p class="text-lg  mt-3 text-secondary-text/80">
          {weddingData.venue}
        </p>
        <p class="text-lg  text-secondary-text/80">
          {weddingData.location}
        </p>
      </div>

      <div class="mb-12">
        <h2 class="text-2xl font-serif text-secondary-text/80 mb-6">Counting Down To Our Big Day</h2>
        <div class="grid grid-cols-2 md:grid-cols-4 gap-4 max-w-md mx-auto">
          <div class="bg-secondary-text/65 backdrop-blur-sm rounded-lg p-4 shadow-lg">
            <div class="text-3xl font-bold text-custom-yellow">{timeLeft.days}</div>
            <div class="text-sm text-custom-yellow uppercase tracking-wide">Days</div>
          </div>
          <div class="bg-secondary-text/65 backdrop-blur-sm rounded-lg p-4 shadow-lg">
            <div class="text-3xl font-bold text-custom-yellow">{timeLeft.hours}</div>
            <div class="text-sm text-custom-yellow uppercase tracking-wide">Hours</div>
          </div>
          <div class="bg-secondary-text/65 backdrop-blur-sm rounded-lg p-4 shadow-lg">
            <div class="text-3xl font-bold text-custom-yellow">{timeLeft.minutes}</div>
            <div class="text-sm text-custom-yellow uppercase tracking-wide">Minutes</div>
          </div>
          <div class="bg-secondary-text/65 backdrop-blur-sm rounded-lg p-4 shadow-lg">
            <div class="text-3xl font-bold text-custom-yellow">{timeLeft.seconds}</div>
            <div class="text-sm text-custom-yellow uppercase tracking-wide">Seconds</div>
          </div>
        </div>
      </div>

      <div class="flex flex-col sm:flex-row gap-4 justify-center items-center">
        <button onclick={rsvp} class="bg-secondary-text/65 hover:bg-primary-text/50 text-custom-yellow px-8 py-3 rounded-full font-semibold transition-all duration-200 transform hover:scale-105 shadow-lg border-2 border-dark-red/5 hover:border-primary-text/5 hover:text-secondary-text/70">
          RSVP Now
        </button>
        <button onclick={registry} class="border-2 border-primary-text/8 text-secondary-text/70 bg-primary-text/60 hover:bg-secondary-text/70 hover:text-custom-yellow px-8 py-3 rounded-full font-semibold transition-all duration-200 transform hover:scale-105 shadow-lg">
          View Registry
        </button>
      </div>
      

      <div class="hidden sm:block absolute bottom-6 md:bottom-8 lg:bottom-12 left-1/2 transform -translate-x-1/2 animate-bounce">
        <div class="bg-white/10 backdrop-blur-sm rounded-full p-3 border border-white/20">
          <svg class="w-5 h-5 md:w-6 md:h-6 text-secondary-text" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path>
          </svg>
        </div>
      </div>
      </div>
    </section>

    <section class="py-16 bg-bg-white">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid md:grid-cols-3 gap-8 text-center">
          <div class="group hover:transform hover:scale-105 transition-all duration-200">
            <div class="w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4 group-hover:bg-dark-red/20">
              <svg class="w-8 h-8 text-primary-text/80" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
            </div>
            <h3 class="text-xl font-semibold text-secondary-text/80 mb-2">When</h3>
            <p class="text-secondary-text/80">{formatDate(weddingData.date)}</p>
            <p class="text-secondary-text/80 text-sm">6:00 PM</p>
          </div>

          <div class="group hover:transform hover:scale-105 transition-all duration-200">
            <div class="w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4 group-hover:bg-dark-red/20">
              <svg class="w-8 h-8 text-primary-text/80" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
              </svg>
            </div>
            <h3 class="text-xl font-semibold text-secondary-text/80 mb-2">Where</h3>
            <p class="text-secondary-text/80">{weddingData.venue}</p>
            <p class="text-secondary-text/80 text-sm">{weddingData.location}</p>
          </div>

          <div class="group hover:transform hover:scale-105 transition-all duration-200">
            <div class="w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4 group-hover:bg-dark-red/20">
              <svg class="w-8 h-8 text-primary-text/80" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
              </svg>
            </div>
            <h3 class="text-xl font-semibold text-secondary-text/80 mb-2">RSVP</h3>
            <p class="text-secondary-text/80">Please respond by</p>
            <p class="text-secondary-text/80 text-sm">Oct 30th, 2025</p>
          </div>
        </div>
      </div>
</div>
