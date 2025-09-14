<script lang="ts">
  import { onMount } from 'svelte';
  import { goto } from "$app/navigation";
  

  const weddingData = {
    bride: 'Medo',
    groom: 'Rawan',
    date: '2025-10-21',
    venue: 'Sunset Garden Estate',
    location: 'Napa Valley, California'
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
      goto("/rsvp")
    }

  async function registry() {
    goto('/registry')
  }


  const navItems = ['Home', 'Our Story', 'Details', 'Registry', 'RSVP'];
</script>

<div class="min-h-screen bg-dark-red/10">
  <section class="relative min-h-screen bg-dark-red/10 flex items-center justify-center px-4">
    <div class="text-center z-10 max-w-4xl mx-auto">
      <div class="mb-8">
        <h1 class="font-serif text-6xl sm:text-7xl lg:text-8xl text-dark-red mb-4 ml-13 leading-tight">
          {weddingData.bride}
          <span class="text-custom-yellow mx-4">&</span>
          {weddingData.groom}
        </h1>
        <div class="w-32 h-1 bg-custom-yellow mx-auto mb-6"></div>
        <p class="text-xl sm:text-2xl text-dark-red font-light mb-2">
          are getting married
        </p>
        <p class="text-lg text-dark-red">
          {formatDate(weddingData.date)}
        </p>
        <p class="text-lg text-dark-red">
          {weddingData.venue}, {weddingData.location}
        </p>
      </div>

      <div class="mb-12">
        <h2 class="text-2xl font-serif text-dark-red mb-6">Counting Down To Our Big Day</h2>
        <div class="grid grid-cols-2 md:grid-cols-4 gap-4 max-w-md mx-auto">
          <div class="bg-dark-red/70 backdrop-blur-sm rounded-lg p-4 shadow-lg">
            <div class="text-3xl font-bold text-custom-yellow">{timeLeft.days}</div>
            <div class="text-sm text-custom-yellow uppercase tracking-wide">Days</div>
          </div>
          <div class="bg-dark-red/70 backdrop-blur-sm rounded-lg p-4 shadow-lg">
            <div class="text-3xl font-bold text-custom-yellow">{timeLeft.hours}</div>
            <div class="text-sm text-custom-yellow uppercase tracking-wide">Hours</div>
          </div>
          <div class="bg-dark-red/70 backdrop-blur-sm rounded-lg p-4 shadow-lg">
            <div class="text-3xl font-bold text-custom-yellow">{timeLeft.minutes}</div>
            <div class="text-sm text-custom-yellow uppercase tracking-wide">Minutes</div>
          </div>
          <div class="bg-dark-red/70 backdrop-blur-sm rounded-lg p-4 shadow-lg">
            <div class="text-3xl font-bold text-custom-yellow">{timeLeft.seconds}</div>
            <div class="text-sm text-custom-yellow uppercase tracking-wide">Seconds</div>
          </div>
        </div>
      </div>

      <div class="flex flex-col sm:flex-row gap-4 justify-center items-center">
        <button onclick={rsvp} class="bg-dark-red/70 hover:bg-custom-yellow/70 text-custom-yellow px-8 py-3 rounded-full font-semibold transition-all duration-200 transform hover:scale-105 shadow-lg border-2 border-dark-red/5 hover:border-custom-yellow/7 hover:text-dark-red">
          RSVP Now
        </button>
        <button onclick={registry} class="border-2 border-custom-yellow/8 text-dark-red bg-custom-yellow/80 hover:bg-dark-red/70 hover:text-custom-yellow px-8 py-3 rounded-full font-semibold transition-all duration-200 transform hover:scale-105 shadow-lg">
          View Registry
        </button>
      </div>

      <div class="hidden sm:block absolute bottom-6 md:bottom-8 lg:bottom-12 left-1/2 transform -translate-x-1/2 animate-bounce">
        <div class="bg-white/10 backdrop-blur-sm rounded-full p-3 border border-white/20">
          <svg class="w-5 h-5 md:w-6 md:h-6 text-dark-red" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path>
          </svg>
        </div>
      </div>
      </div>
    </section>

    <section class="py-16 bg-dark-red/10">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid md:grid-cols-3 gap-8 text-center">
          <div class="group hover:transform hover:scale-105 transition-all duration-200">
            <div class="w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4 group-hover:bg-dark-red/20">
              <svg class="w-8 h-8 text-dark-red/80" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
            </div>
            <h3 class="text-xl font-semibold text-dark-red/80 mb-2">When</h3>
            <p class="text-dark-red/80">{formatDate(weddingData.date)}</p>
            <p class="text-dark-red/80 text-sm">4:00 PM Ceremony</p>
          </div>

          <div class="group hover:transform hover:scale-105 transition-all duration-200">
            <div class="w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4 group-hover:bg-dark-red/20">
              <svg class="w-8 h-8 text-dark-red/80" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
              </svg>
            </div>
            <h3 class="text-xl font-semibold text-dark-red/80 mb-2">Where</h3>
            <p class="text-dark-red/80">{weddingData.venue}</p>
            <p class="text-dark-red/80 text-sm">{weddingData.location}</p>
          </div>

          <div class="group hover:transform hover:scale-105 transition-all duration-200">
            <div class="w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4 group-hover:bg-dark-red/20">
              <svg class="w-8 h-8 text-dark-red/80" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
              </svg>
            </div>
            <h3 class="text-xl font-semibold text-dark-red/80 mb-2">RSVP</h3>
            <p class="text-dark-red/80">Please respond by</p>
            <p class="text-dark-red/80 text-sm">May 15th, 2024</p>
          </div>
        </div>
      </div>
</div>
