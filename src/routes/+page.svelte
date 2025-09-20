<script lang="ts">
  import { onMount } from "svelte";
  import { writable } from "svelte/store";
  import { goto } from "$app/navigation";

  const code1: string = "test1";
  const code2: string = "test2";
  const code3: string = "test3";
  
  let password: string = $state("");
  let showForm: boolean = $state(false);

  async function login(): Promise<void> {
    if (password === code1) {
      goto("/password1/home");
    } else if (password == code2) {
      goto("/password2/home")
    } else if (password == code3) {
      goto("/password3/home")
    }
    else {
      alert('Wrong Password, GET YA ASS OUTTA HERE!');
    }
  }

  function handleKeyPress(event: KeyboardEvent): void {
    if (event.key === 'Enter') {
      login();
    }
  }

  // Handle mobile tap/click
  function toggleForm(): void {
    showForm = !showForm;
  }
</script>

<div class="min-h-screen flex items-center justify-center bg-dark-red/30 p-4">
  <!-- Main container with responsive sizing -->
  <div class="relative w-full 
    max-w-sm sm:max-w-md md:max-w-lg lg:max-w-2xl xl:max-w-3xl
    aspect-[4/3]
    group"
    role="button"
    tabindex="0"
    onclick={toggleForm}
    onkeypress={(e) => e.key === 'Enter' && toggleForm()}
  >
    <!-- Image with hover effect -->
    <img 
      src="wedding-photo-placeholder.jpg" 
      class="absolute inset-0 w-full h-full object-cover rounded-xl shadow-xl
        transition-opacity duration-500 
        group-hover:opacity-0
        {showForm ? 'opacity-0' : 'opacity-100'}
        md:opacity-100 md:group-hover:opacity-0"
      alt="Wedding photo"
    >
    
    <!-- Password form overlay -->
    <div class="absolute inset-0 flex flex-col items-center justify-center p-4 space-y-4">
      <input 
        type="password" 
        placeholder="Enter password"
        bind:value={password}
        onkeypress={handleKeyPress}
        class="w-full max-w-xs 
          px-3 py-2 sm:px-4 sm:py-3 
          text-sm sm:text-base lg:text-lg 
          border border-gray-300 rounded-lg 
          focus:outline-none focus:ring-2 focus:ring-dark-red/80 focus:border-transparent 
          shadow-sm bg-white 
          transition-opacity duration-500
          {showForm ? 'opacity-100' : 'opacity-0'}
          md:opacity-0 md:group-hover:opacity-100"
      >
      <button 
        type="submit"
        onclick={(e) => {
          e.stopPropagation();
          login();
        }}
        class="w-full max-w-xs 
          px-3 py-2 sm:px-4 sm:py-3 
          text-sm sm:text-base lg:text-lg 
          bg-dark-red hover:bg-dark-red/80 text-light-yellow 
          rounded-lg 
          focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 
          shadow-sm 
          transition-all duration-500
          {showForm ? 'opacity-100' : 'opacity-0'}
          md:opacity-0 md:group-hover:opacity-100
          active:scale-95"
      >
        Enter
      </button>
    </div>
  </div>
</div>