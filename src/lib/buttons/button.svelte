<script>
   

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
  
   
    <div class="container">
      <h1 style="font-size: 29px; color: white; margin-top: 70px;" >ATS</h1>
      <div class="mb-6">
    <i class="fa fa-mortar-board" on:click={candidatelist} style="font-size: 26px; color: white; margin-top: 45px;">Candidates</i>
      </div>
      <div class="mb-6">
    <i class="fa fa-briefcase"   on:click={joblist} style="font-size: 26px; color: white; margin-top: 30px;" >Jobs</i>
      </div>
  </div>
</main>
<div class="container2">
<Profile/>
</div>
  <style>
 
 

    /* Style for the containers */
    .container {
  background-color: rgb(113, 113, 246);
  padding: 20px;
  border-radius: 5px;
  width: 172px;
  height: 745px;
  margin-top: -90px;
  position:absolute;
}

.container2 {
    background-color: rgb(113, 113, 246);
  padding: 20px;
  border-radius: 5px;
  width: 1535px;
  height: 70px;
  margin-top: -90px;
  position: absolute;
}


  
 
  </style>
  