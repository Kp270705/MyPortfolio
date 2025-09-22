<script>
  import { Navbar, NavBrand, NavLi, NavUl, NavHamburger, } from "flowbite-svelte";

  import { fly } from "svelte/transition";

  import { link } from "svelte-spa-router";

  import Darkmode from "../../components/Darkmode/Darkmode.svelte";

  // import staric content

  import Rocket from "../../assets/icons/rocket1.png";

  let pages = [
    { name: "Home", path: "/" },

    { name: "About", path: "/about" },
  ];
</script>

<Navbar class="fixed top-0 w-full z-50 bg-white/10 dark:bg-gray-900/80 backdrop-blur-md border-b border-gray-200 dark:border-gray-700" >
  <NavBrand href="/">
    <img src={Rocket} class="me-3 h-6 sm:h-9" alt="Logo" />

    <span class="self-center text-xl font-semibold whitespace-nowrap dark:text-white">Kunal</span>
  </NavBrand>

  <NavHamburger />

  <NavUl>
    {#each pages as page}
      <NavLi>
        <a
          use:link
          href={page.path}
          class="block py-2 px-3 text-blue-700 hover:bg-gray-100 dark:text-gray-400 dark:hover:bg-gray-700">
          {page.name}
        </a>
      </NavLi>
    {/each}

    <NavLi>
      <Darkmode />
    </NavLi>
  </NavUl>


</Navbar>
