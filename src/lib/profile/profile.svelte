<script>
  import { goto } from '$app/navigation';
  import { auth } from '$lib/firebase/firebase.js';
  import { Button, Dropdown, DropdownItem,  } from 'flowbite-svelte';
  let showModal = false;

  function openModal() {
    showModal = true;
  }

  function closeModal() {
    showModal = false;
  }

  function handleLogout() {
  // Display a confirmation dialog
  const confirmLogout = window.confirm("Are you sure you want to logout?");
  
  if (confirmLogout) {
    // User confirmed, proceed with logout
    // You can use your Firebase auth instance to sign the user out
    // For example:
    auth.signOut().then(() => {
      // Handle successful logout, e.g., navigate to the /information page
      console.log("User logged out");
      goto('/'); // Navigate to the /information route
    }).catch((error) => {
      // Handle logout error, if any
      console.error("Logout error:", error);
    });
  }
}


  function Businessprofile() {
    goto('/businessprofile');
  }
</script>
 
<img class="imag" src="https://i.stack.imgur.com/YQu5k.png" alt="Click me" on:click={openModal} />

 <Dropdown style="height: 200px; width:200px" >
        <div slot="header" class="px-12 py-2">
         
          <span class="block truncate text-sm font-medium"  style="color: crimson; font-size:large">Hire Optica</span>
        </div>
        <DropdownItem class="fa fa-building" style="font-size:18px"  on:click={Businessprofile} >Business Profile</DropdownItem>
      
      
        <DropdownItem class="blue-text" slot="footer" on:click={handleLogout} >Logout</DropdownItem>
       
      </Dropdown>



<style>
 .imag {
  position: absolute;
  top: 10px;
  right: 25px;
  height: 50px;
}



</style>
