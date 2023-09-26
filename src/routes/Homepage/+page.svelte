<script>
  import { Card } from 'flowbite-svelte';
  import { auth } from '$lib/firebase/firebase.js';
import { goto } from '$app/navigation';
import Profile from "$lib/profile/profile.svelte"


  
// Function to handle logout
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

function candidatelist() {
  goto('/candidatelist');
}
function joblist() {
  goto('/joblist');
}




</script>

<main>

    
<h1 class="h1" style="color:red;">Welcome to Hire optica</h1>

<div class="container">
    <h1 style="font-size: 29px; color: white; margin-top: 70px;" >ATS</h1>
    <div class="mb-6">
  <i class="fa fa-mortar-board" on:click={candidatelist} style="font-size: 26px; color: white; margin-top: 45px;cursor:pointer;">Candidates</i>
    </div>
    <div class="mb-6">
  <i class="fa fa-briefcase"   on:click={joblist} style="font-size: 26px; color: white; margin-top: 30px;cursor:pointer;" >Jobs</i>
    </div>
</div>
</main>
<div class="container2">
<Profile/>
</div>
<style>

.container {
      background-color: rgb(113, 113, 246);
      padding: 20px;
     border-radius: 5px;
     width:172px;
     height: 735px;
     margin-top:10px;
  }
  .h1{
    position: absolute;
    top:200px;
    left: 500px;
    font-size:80px;
  }
  .container2 {
    background-color: rgb(113, 113, 246);
      padding: 20px;
     border-radius: 5px;
     width: 1535px;
     height: 70px;
     margin-top:-745px;
  }




</style>
