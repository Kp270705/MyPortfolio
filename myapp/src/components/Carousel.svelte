<script>
  import { Carousel } from "flowbite-svelte";
  import { images } from "../jsContent/carousleContent.js";
</script>

<div style="height: 400px;">
    <Carousel {images} duration={3000} />
</div>

