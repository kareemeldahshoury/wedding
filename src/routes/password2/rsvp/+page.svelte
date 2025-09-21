<script lang='ts'>
  import { goto } from "$app/navigation";


  let attending = $state('');
  let pluses = $state('');
  let confirmPassword = $state('');
  let firstName = $state('');
  let lastName = $state('');
  let submitted = $state(false);

  async function submitRSVP() {
    // submitted = true;
    // try {
    //     const formData = {
    //           name: firstName,
    //           email: lastName,
    //           attending: attending,
    //           pluses: pluses
    //       };

    //     console.log('Submitting form data:', formData);
    //     const response = await fetch('https://script.google.com/macros/s/AKfycbwRXcLpxQP12k4iLfjO-uFZ99dHDgUGshcgpDCWUCV_iN6feX3Uy1VabRg3WBz5ldLyRQ/exec', {
    //         method: 'POST',
    //         body: JSON.stringify(formData)
    //     });

    //     const result = await response.text();
    //     console.log('Response:', result);
        
    //     try {
    //         const res = JSON.parse(result);
    //         if (res.success) {
    //             alert('RSVP submitted successfully!');
    //             goto('/registry')
    //         } else {
    //             alert('Error: ' + res.error);
    //             submitted = false;
    //         }
    //     } catch (parseError) {
    //         console.log('Response was not JSON:', result);
    //         alert('Form submitted (response not JSON)');
    //         goto('/home');
    //     }
        
    // } catch (error) {
    //     console.error('Error:', error);
    //     alert('Error submitting RSVP: ' + error.message);
    //     submitted = false;
    // }
    window.open('https://docs.google.com/forms/d/e/1FAIpQLSc_zA8dPAU-cKPtNGL5s5xv97txogXqfw-al_jeUMm5Dcx1rQ/viewform?usp=header', '_blank')
    goto('/password2/registry')
}


</script>

<div class="min-h-screen w-full flex flex-col justify-center items-center bg-bg-white">
  <img src="/flower_rsvp.svg" 
  class="absolute left-2 hidden sm:block md:left-6 lg:left-8 top-1/2 -translate-y-1/2 w-48 h-48 sm:w-56 sm:h-56 md:w-64 md:h-64 lg:w-80 lg:h-80 xl:w-96 xl:h-96 opacity-40 sm:opacity-45 md:opacity-50" 
  alt="Floral decoration" />
  <img src="/flower_rsvp.svg" 
  class="absolute left-2 hidden sm:block md:left-6 lg:left-8 top-1/2 -translate-y-1/2 w-48 h-48 sm:w-56 sm:h-56 md:w-64 md:h-64 lg:w-80 lg:h-80 xl:w-96 xl:h-96 opacity-40 sm:opacity-45 md:opacity-50" 
  alt="Floral decoration" />


<!-- Right side floral (flipped) -->
  <img src="/flower_rsvp.svg" 
    class="absolute right-2 hidden sm:block md:right-6 lg:right-8 top-1/2 -translate-y-1/2 w-48 h-48 sm:w-56 sm:h-56 md:w-64 md:h-64 lg:w-80 lg:h-80 xl:w-96 xl:h-96 opacity-40 sm:opacity-45 md:opacity-50 scale-x-[-1]" 
    alt="Floral decoration" />
    <img src="/flower_rsvp.svg" 
    class="absolute right-2 hidden sm:block md:right-6 lg:right-8 top-1/2 -translate-y-1/2 w-48 h-48 sm:w-56 sm:h-56 md:w-64 md:h-64 lg:w-80 lg:h-80 xl:w-96 xl:h-96 opacity-40 sm:opacity-45 md:opacity-50 scale-x-[-1]" 
    alt="Floral decoration" />
  <h1 class="text-8xl text-primary-text font-script">RSVP!</h1>
  <p class="mt-10 w-52 text-lg text-center sm:text-sm md:text-md lg:text-lg text-secondary-text font-light mb-2">
    Please RSVP for the wedding by filling out the google form!
  </p>
  <div class="space-y-6">
    <!-- <div>
      <label class="block text-lg text-center text-light-yellow font-medium mb-2 mt-5">What is your first name?</label>
      <input type="text" 
        placeholder="First Name" 
        class="w-full px-4 py-3 text-lg bg-custom-white border border-light-yellow/7 rounded-lg focus:outline-none focus:ring-3 focus:ring-light-yellow focus:border-transparent shadow-sm" 
        bind:value={firstName}
      />
    </div>
  
    <div>
      <label class="block text-lg text-center font-medium text-light-yellow mb-2">What is your last name?</label>
      <input type="text" 
        placeholder="Last Name" 
        class="w-full px-4 py-3 text-lg bg-custom-white border border-light-yellow/7 rounded-lg focus:outline-none focus:ring-3 focus:ring-light-yellow focus:border-transparent shadow-sm" 
        bind:value={lastName}
      />
    </div>
  
    <div>
      <label class="block text-sm sm:text-base md:text-lg text-center font-medium text-light-yellow mb-2 sm:mb-3">
        Are you coming?
      </label>
      <select 
        class="w-full px-3 py-2 sm:px-4 sm:py-3 text-sm sm:text-base md:text-lg bg-custom-white border border-light-yellow/7 rounded-lg focus:outline-none focus:ring-2 sm:focus:ring-3 focus:ring-light-yellow focus:border-transparent shadow-sm transition-all duration-200 appearance-none cursor-pointer" 
        bind:value={attending}
      >
        <option value="" disabled selected>Please select...</option>
        <option value="Yes">Yes</option>
        <option value="No">No</option>
      </select>
    </div>
  
    <div>
      <label class="block text-lg text-center font-medium text-light-yellow mb-2">How many people are you bringing?</label>
      <input type="number" 
        placeholder="Number of +1's" 
        class="w-full px-4 py-3 text-lg bg-custom-white border border-light-yellow/7 rounded-lg focus:outline-none focus:ring-3 focus:ring-light-yellow focus:border-transparent shadow-sm" 
        bind:value={pluses}
      />
    </div>

  </div> -->

  <div>
    <div class="flex space-x-4 mt-10">
      <button on:click={submitRSVP} class="bg-secondary-text/65 hover:bg-primary-text/50 text-custom-yellow px-8 py-3 rounded-full font-semibold transition-all duration-200 transform hover:scale-105 shadow-lg border-2 border-dark-red/5 hover:border-primary-text/5 hover:text-secondary-text/70">
          RSVP Now
      </button>
    </div>  
  
    {#if submitted}
    <div class="flex space-x-4 mt-10 items-center">
      <h1 class="text-xl text-light-yellow leading-relaxed mb-20">Submitting ...</h1>
    </div>   
    {/if}
  </div>
</div>
</div>