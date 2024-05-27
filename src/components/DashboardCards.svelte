<script>
  import { goto } from "$app/navigation";
  export let card_link;
  export let card_title;
  export let card_description;
  export let card_svg;

  const onClickLink = (link) => {
    goto(link, { replaceState: false });
  };
</script>

<article
  class="rounded-lg border border-gray-100 bg-white p-4 shadow-sm transition hover:shadow-lg sm:p-6"
>
  <span class="inline-block rounded bg-blue-600 p-2 text-white">
    {@html card_svg}
  </span>

  <h3 class="mt-0.5 text-lg font-medium text-gray-900">
    {card_title}
  </h3>

  <p class="mt-2 line-clamp-3 text-sm/relaxed text-gray-500">
    {card_description}
  </p>

  <button
    on:click={() => onClickLink(card_link)}
    id={`${card_title}-card`}
    class="group mt-4 inline-flex items-center gap-1 text-sm font-medium text-blue-700"
  >
    Find out more &rarr;
  </button>
</article>
