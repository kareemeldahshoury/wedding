<script>
  import { goto } from "$app/navigation";


  let attending = $state('');
  let pluses = $state('');
  let confirmPassword = $state('');
  let firstName = $state('');
  let lastName = $state('');
  

  async function submitRSVP() {
    try {

        const formData = {
              name: firstName,
              email: lastName,
              attending: attending,
              pluses: pluses
          };

        console.log('Submitting form data:', formData);

        const response = await fetch('https://script.google.com/macros/s/AKfycbwRXcLpxQP12k4iLfjO-uFZ99dHDgUGshcgpDCWUCV_iN6feX3Uy1VabRg3WBz5ldLyRQ/exec', {
            method: 'POST',
            body: JSON.stringify(formData)
        });

        const result = await response.text();
        console.log('Response:', result);
        
        try {
            const res = JSON.parse(result);
            if (res.success) {
                alert('RSVP submitted successfully!');
            } else {
                alert('Error: ' + res.error);
            }
        } catch (parseError) {
            console.log('Response was not JSON:', result);
            alert('Form submitted (response not JSON)');
        }
        
    } catch (error) {
        console.error('Error:', error);
        alert('Error submitting RSVP: ' + error.message);
    }
}

</script>

<div class="h-screen w-full flex flex-col justify-center items-center bg-dark-red/70">
  <h1 class="text-8xl text-light-yellow">Sign Up</h1>
  <p class="mt-10 w-52 text-lg text-center sm:text-sm md:text-md lg:text-lg text-light-yellow font-light mb-2">
    Please RSVP for the wedding by answering the questions below!
  </p>
  <div class="space-y-6">
    <div>
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
      <label class="block text-lg text-center font-medium text-light-yellow mb-2">Are you coming?</label>
      <input type="email" 
        placeholder="Yes or No" 
        class="w-full px-4 py-3 text-lg bg-custom-white border border-light-yellow/7 rounded-lg focus:outline-none focus:ring-3 focus:ring-light-yellow focus:border-transparent shadow-sm" 
        bind:value={attending}
      />
    </div>
  
    <div>
      <label class="block text-lg text-center font-medium text-light-yellow mb-2">How many people are you bringing?</label>
      <input type="text" 
        placeholder="Number of +1's" 
        class="w-full px-4 py-3 text-lg bg-custom-white border border-light-yellow/7 rounded-lg focus:outline-none focus:ring-3 focus:ring-light-yellow focus:border-transparent shadow-sm" 
        bind:value={pluses}
      />
    </div>
  
    <!-- <div>
      <label class="block text-lg text-center font-medium text-gray-700 mb-2">Are you </label>
      <input type="password" 
        placeholder="Re-enter your password" 
        class="w-full px-4 py-3 text-lg border border-gray-300 rounded-lg focus:outline-none focus:ring-3 focus:ring-usfaaf-blue focus:border-transparent shadow-sm" 
        bind:value={confirmPassword}
      />
    </div> -->
  </div>

  <div class="flex space-x-4 mt-10">
    <button onclick={submitRSVP} class="bg-custom-white/70 text-dark-red px-8 py-3 rounded-full font-semibold transition-all duration-200 transform hover:scale-105 shadow-lg border-2 border-light-yellow/5 hover:border-light-yellow/7">
      RSVP Now
    </button>
  </div>
</div>