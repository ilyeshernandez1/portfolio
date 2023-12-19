<script lang="ts">
  import { animate } from "motion";
	import { onMount } from "svelte";

  onMount(() => {
    animate("#logo", {
      y: ["100%", 0],
      skewX: [10, 0]
    }, {
      delay: 0.5,
      easing: [0.17, 0.77, 0.77, 1]
    })
    
  })
</script>

<header class="bg-black/75 backdrop-blur-xl sticky z-10 top-0 left-0 flex justify-center mx-10 py-4">
  <div class="overflow-hidden">
    <span id="logo" class="font-bold inline-block font-serif text-2xl">Ilyes.</span>
  </div>
</header>