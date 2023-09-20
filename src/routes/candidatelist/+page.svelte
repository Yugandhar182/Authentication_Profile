
<script>
  import { onMount } from "svelte";
  import { auth } from '$lib/firebase/firebase.js';
 import { goto } from '$app/navigation';

 import Button from "$lib/buttons/button.svelte";

 
 let jsonData = [];
 let gridData = [];
 
 onMount(async () => {
   const response = await fetch(
     "https://api.recruitly.io/api/candidate?apiKey=TEST9349C0221517DA4942E39B5DF18C68CDA154"
   );
   const responseData = await response.json();
   jsonData = responseData.data;
 
   gridData = jsonData.map((item) => ({
     id: item.id,
     firstName: item.firstName,
     surname: item.surname,
     email: item.email,
     mobile: item.mobile,
   }));
 
   const dataGrid = new DevExpress.ui.dxDataGrid(document.getElementById("dataGrid"), {
     dataSource: gridData,
     columns: [
       { dataField: "id", caption: "ID", width: 300  },
       { dataField: "firstName", caption: "Full Name", width: 220 },
       { dataField: "surname", caption: "Surname", width: 220 },
       { dataField: "email", caption: "Email", width: 220 },
       { dataField: "mobile", caption: "Mobile", width:220 },
       // Define other columns as needed
     ],
     showBorders: true,
     showColumnLines:true,
     showRowLines: true,

     rowAlternationEnabled: true,
     filterRow: {
       visible: true,
     },
     summary: {
           groupItems: [{
               summaryType: "count"
           }]
       },
     editing: {
       allowDeleting: true,
       allowAdding: true,
       allowUpdating: true,
       mode: "popup",
       form: {
         labelLocation: "top",
       },
       popup: {
         showTitle: true,
         
       },
       texts: {
         saveRowChanges: "Save",
         cancelRowChanges: "Cancel",
         deleteRow: "Delete",
         confirmDeleteMessage: "Are you sure you want to delete this record?",
       },
     },
     paging: {
       pageSize: 13,
     },
     rowHeight: 2550,
     columnAutoWidth: true,
     onRowInserting: async (e) => {
       console.log("Data being sent to API:", e.data);
       try {
         const response = await fetch(
           "https://api.recruitly.io/api/candidate?apiKey=TEST27306FA00E70A0F94569923CD689CA9BE6CA",
           {
             method: "POST",
             headers: {
               "Content-Type": "application/json",
             },
             body: JSON.stringify(e.data),
           }
         );
 
         const responseData = await response.json();
         if (response.ok) {
           e.data.firstName = responseData.firstName;
           gridData.push(e.data);
           dataGrid.refresh();
         } else {
           console.error("Failed to add record:", responseData.error);
         }
       } catch (error) {
         console.error("Failed to add record:", error);
       }
     },
     onRowUpdating: async (e) => {
       try {
         console.log(e);
         var newData = {
           id: e.key.id,
           firstName: e.newData.firstName === undefined ? e.oldData.firstName : e.newData.firstName,
           surname: e.newData.surname === undefined ? e.oldData.surname : e.newData.surname,
           email: e.newData.email === undefined ? e.oldData.email : e.newData.email,
           mobile: e.newData.mobile === undefined ? e.oldData.mobile : e.newData.mobile,
         }
 
         console.log(newData)
         const response = await fetch(
           `https://api.recruitly.io/api/candidate?apiKey=TEST9349C0221517DA4942E39B5DF18C68CDA154`,
           {
             method: "POST",
             headers: {
               "Content-Type": "application/json",
             },
             body: JSON.stringify(newData),
           }
         );
         const responseData = await response.json();
         if (response.ok) {
           const updatedItemIndex = gridData.findIndex((item) => item.id === e.key);
           gridData.push(e.newData);
           gridData[updatedItemIndex] = e.newData;
           dataGrid.refresh();
         } else {
           console.error("Failed to update record:", responseData.error);
         }
       } catch (error) {
         console.error("Failed to update record:", error);
       }
     },
     onRowRemoving: async (e) => {
       console.log("Data being sent to API:", e.data);
       try {
         const response = await fetch(
           `https://api.recruitly.io/api/candidate/${e.data.id}?apiKey=TEST27306FA00E70A0F94569923CD689CA9BE6CA`,
           {
             method: "DELETE",
           }
         );
         if (response.ok) {
           const removedItemIndex = gridData.findIndex((item) => item.id === e.key);
           if (removedItemIndex > -1) {
             gridData.splice(removedItemIndex, 1);
             dataGrid.refresh();
           }
         } else {
           console.error("Failed to delete record.");
         }
       } catch (error) {
         console.error("Failed to delete record:", error);
       }
     },
     onInitialized: () => {
 
     },
   });
 });
 let email = ''; // Define email in a scope accessible to the entire script
 


 let isBlue = true; 

 onMount(() => {
   // Create an interval to toggle the color every 2 seconds
   const interval = setInterval(() => {
     isBlue = !isBlue;
   }, 1000);

   // Clean up the interval when the component is unmounted
   return () => clearInterval(interval);
 });

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


 function Homepage() {
   goto('/Homepage');
 }





</script>



<main >
 <Button/>
 <h2 class="h2" style="color: blue;">candidate list</h2>
 <div id="dataGrid" class="datagrid-container"></div>
 <i class="fa fa-home" style="font-size:35px;color:white; position: absolute; top: 10px; left: 15px;" on:click={Homepage}></i>
</main>




<style>
 .datagrid-container{
    margin-top:10px ;
    margin-right:5px;
    margin-left: 200px;
    height: 620px;
    width: 1330px;
   }
 


  .h2 {
   margin-left: 700px;
   margin-top: 80px;
   font-weight: bold;
   font-size: 15px;
 
 }
 

</style>