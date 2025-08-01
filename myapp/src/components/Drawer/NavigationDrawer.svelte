<script>
  import { Drawer, Button, CloseButton, Sidebar, SidebarWrapper, SidebarDropdownWrapper, SidebarGroup, SidebarItem } from "flowbite-svelte";
  import { ChartPieSolid, CartSolid, GridSolid, MailBoxSolid, UsersSolid, ShoppingBagSolid, ArrowRightToBracketOutline, EditOutline } from "flowbite-svelte-icons";
  let hidden2 = $state(true);
  let spanClass = "flex-1 ms-3 whitespace-nowrap";
  import Darkmode from "../Darkmode.svelte";;

</script>

<div class="text-center align-initial">
  <Button onclick={() => (hidden2 = false)}>Navigation Menu</Button>
</div>
<Drawer bind:hidden={hidden2} class="w-64 bg-gray-50 p-0 dark:bg-gray-800">
  <div class="flex items-center justify-between px-2 pt-4">
    <h5 class="px-4 text-base font-semibold text-gray-500 uppercase dark:text-gray-400">Menu</h5>
    <CloseButton onclick={() => (hidden2 = true)} class="dark:text-white" />
  </div>
  <Sidebar disableBreakpoints={true} class="top-16">
    <SidebarWrapper class="overflow-y-auto rounded-sm px-3 py-0 dark:bg-gray-800">
      <SidebarGroup>

        <SidebarItem label="">
          {#snippet icon()}
            <Darkmode />
          {/snippet}
        </SidebarItem>

        <SidebarItem label="Sign In">
          {#snippet icon()}
            <ArrowRightToBracketOutline class="h-5 w-5 text-gray-500 transition duration-75 group-hover:text-gray-900 dark:text-gray-400 dark:group-hover:text-white" />
          {/snippet}
        </SidebarItem>

        <SidebarItem label="Sign Up">
          {#snippet icon()}
            <EditOutline class="h-5 w-5 text-gray-500 transition duration-75 group-hover:text-gray-900 dark:text-gray-400 dark:group-hover:text-white" />
          {/snippet}
        </SidebarItem>

      </SidebarGroup>
    </SidebarWrapper>
  </Sidebar>
</Drawer>