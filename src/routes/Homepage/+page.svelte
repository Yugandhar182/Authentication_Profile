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
  
  <div class="card-container">
    <div class="grid grid-cols-3 gap-4">
      <Card class="small-card" style="width: 350px ;  "  >
        <h5 class="mb-2 text-xl font-bold tracking-tight text-gray-900 dark:text-white"  >Revenue</h5>
        
        <p class="font-normal text-gray-700 dark:text-gray-400 leading-tight">£6,283,954.</p>
      </Card>
      <Card class="small-card" style="width: 350px ;background-color:green  "  >
        <h5 class="mb-2 text-xl font-bold tracking-tight text-gray-900 dark:text-white" style="color: white ; " >Productivity</h5>
        <p class="font-normal text-gray-700 dark:text-gray-400 leading-tight" style="color: white ; ">£2,094,651.</p>
      </Card>
      <Card class="small-card" style="width: 350px ; " >
        <h5 class="mb-2 text-xl font-bold tracking-tight text-gray-900 dark:text-white" style="color: blue ; ">Jobs On</h5>
        <p class="font-normal text-gray-700 dark:text-gray-400 leading-tight">54</p>
      </Card>
      <Card class="small-card" style="width: 350px ; " >
        <h5 class="mb-2 text-xl font-bold tracking-tight text-gray-900 dark:text-white" style="color: green ; ">Placements</h5>
        <p class="font-normal text-gray-700 dark:text-gray-400 leading-tight">49</p>
      </Card>
      <Card class="small-card" style="width: 350px ; " >
        <h5 class="mb-2 text-xl font-bold tracking-tight text-gray-900 dark:text-white" style="color: red; ">Invoice Not Sent</h5>
        <p class="font-normal text-gray-700 dark:text-gray-400 leading-tight">£301,192</p>
      </Card>
      <Card class="small-card" style="width: 350px ; background-color:Violet" >
        <h5 class="mb-2 text-xl font-bold tracking-tight text-gray-900 dark:text-white" style="color: white ; ">Andy. Barnes</h5>
        <p class="font-normal text-gray-700 dark:text-gray-400 leading-tight">£6,202,725</p>
      </Card>
      <Card class="small-card" style="width: 350px ;  "  >
        <h5 class="mb-2 text-xl font-bold tracking-tight text-gray-900 dark:text-white" >Invoiced</h5>
        <p class="font-normal text-gray-700 dark:text-gray-400 leading-tight" >£194,735</p>
      </Card>
      <Card class="small-card" style="width: 350px ; " >
        <h5 class="mb-2 text-xl font-bold tracking-tight text-gray-900 dark:text-white" style="color: green ; ">Interviews  </h5>
        <p class="font-normal text-gray-700 dark:text-gray-400 leading-tight">0</p>
      </Card>
      <Card class="small-card" style="width: 350px ;" >
        <h5 class="mb-2 text-xl font-bold tracking-tight text-gray-900 dark:text-white" style="color: blue ; ">CV Shares  </h5>
        <p class="font-normal text-gray-700 dark:text-gray-400 leading-tight" style="color:blue ; ">132</p>
      </Card>
    </div>
  </div>
  
  
   
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
 
  .card-container {
        margin-left: 250px;
        margin-top: 200px;
        height: 100%;
 
    }

    .container {
        background-color: rgb(113, 113, 246);
        padding: 20px;
       border-radius: 5px;
       width:172px;
       height: 745px;
       margin-top:-550px;
    }
    .container2 {
      background-color: rgb(113, 113, 246);
        padding: 20px;
       border-radius: 5px;
       width: 1535px;
       height: 70px;
       margin-top:-744px;
    }


  
 
  </style>
  