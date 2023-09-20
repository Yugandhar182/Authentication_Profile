<script>
    import { Button, Dropdown, DropdownItem,  } from 'flowbite-svelte';
  
  </script>
  
  <Button>Dropdown button</Button>
  <Dropdown>
    <div slot="header" class="px-4 py-2">
      <span class="block text-sm text-gray-900 dark:text-white">Bonnie Green</span>
      <span class="block truncate text-sm font-medium">name@flowbite.com</span>
    </div>
    <DropdownItem>Dashboard</DropdownItem>
    <DropdownItem>Settings</DropdownItem>
    <DropdownItem>Earnings</DropdownItem>
    <DropdownItem slot="footer">Sign out</DropdownItem>
  </Dropdown>