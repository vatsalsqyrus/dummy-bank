<script>
  import { browser } from "$app/environment";

  const goBack = () => {
    if (browser) {
      window.history.back();
    }
  };
</script>

<button class="bg-blue-500 text-white mt-2 text-sm px-2 py-1 rounded-md" on:click={goBack}
  >Back</button
>
