<script>
   

  import { goto } from '$app/navigation';
  import Profile from "$lib/profile/profile.svelte"


    

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
      background-color:rgb(45, 36, 220);
  padding: 20px;
  border-radius: 5px;
  width: 172px;
  height: 745px;
  margin-top: -90px;
  position:absolute;
}

.container2 {
  background-color:rgb(45, 36, 220);
  padding: 20px;
  border-radius: 5px;
  width: 1535px;
  height: 70px;
  margin-top: -80px;
  position: absolute;
}


  
 
  </style>
  
