<script>
  import { onMount } from "svelte";
  import { writable } from "svelte/store";
  import { goto } from "$app/navigation";


  const code = "KingReem02";
  let password = $state("");


  async function login() {
      if (password == code){
        goto("/home")
      }
      else{
        alert('Wrong Password, GET YA ASS OUTTA HERE!');
      }
    }



</script>
<div class="min-h-screen flex flex-col items-center justify-center bg-dark-red/30">
  <div class="relative mb-8 sm:mb-12 md:mb-16 lg:mb-20
    w-80 h-60       
    sm:w-96 sm:h-72  
    md:w-[32rem] md:h-96  
    lg:w-[40rem] lg:h-[30rem]  
    xl:w-[64rem] xl:h-[48rem]  
    mx-auto group">
    
    <img 
      src="wedding-photo-placeholder.jpg" 
      class="w-full h-full object-cover group-hover:opacity-0 duration-500 shadow-xl rounded-xl"
      alt="Wedding photo"
    >
    

    <div class="absolute inset-0 flex flex-col items-center justify-center p-4 space-y-4">
      <input 
        type="password" 
        placeholder="Enter password"
        bind:value={password}
        class="w-full max-w-xs px-4 py-3 text-lg border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-dark-red/80 focus:border-transparent shadow-sm bg-white opacity-0 group-hover:opacity-100 duration-500"
      >
      <button 
        type="submit"
        onclick={login}
        class="w-full max-w-xs px-4 py-3 text-lg bg-dark-red hover:bg-dark-red/80 text-light-yellow rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 shadow-sm opacity-0 group-hover:opacity-100 duration-500"
      >
        Enter
      </button>
    </div>

  </div>
</div>