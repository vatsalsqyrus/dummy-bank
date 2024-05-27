<script>
  import DashboardCards from "../../components/DashboardCards.svelte";
  let cards = [
    {
      card_title: "Loan Management",
      card_description:
        "Efficiently manage all your loan needs in one place. Explore various loan options, apply with ease, and track your loan status to stay updated. Tailored solutions for home, personal, and educational purposes.",
      card_link: "/loans",
      card_svg: `<svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24" {...$$props}>
            <g fill="none" stroke="currentColor" stroke-width="1.5">
                <path d="M17.414 10.414C18 9.828 18 8.886 18 7c0-1.886 0-2.828-.586-3.414m0 6.828C16.828 11 15.886 11 14 11h-4c-1.886 0-2.828 0-3.414-.586m10.828 0Zm0-6.828C16.828 3 15.886 3 14 3h-4c-1.886 0-2.828 0-3.414.586m10.828 0Zm-10.828 0C6 4.172 6 5.114 6 7c0 1.886 0 2.828.586 3.414m0-6.828Zm0 6.828ZM13 7a1 1 0 1 1-2 0a1 1 0 0 1 2 0Z" />
                <path stroke-linecap="round" d="M18 6a3 3 0 0 1-3-3m3 5a3 3 0 0 0-3 3M6 6a3 3 0 0 0 3-3M6 8a3 3 0 0 1 3 3m-4 9.388h2.26c1.01 0 2.033.106 3.016.308a14.85 14.85 0 0 0 5.33.118c.868-.14 1.72-.355 2.492-.727c.696-.337 1.549-.81 2.122-1.341c.572-.53 1.168-1.397 1.59-2.075c.364-.582.188-1.295-.386-1.728a1.887 1.887 0 0 0-2.22 0l-1.807 1.365c-.7.53-1.465 1.017-2.376 1.162c-.11.017-.225.033-.345.047m0 0a8.176 8.176 0 0 1-.11.012m.11-.012a.998.998 0 0 0 .427-.24a1.492 1.492 0 0 0 .126-2.134a1.9 1.9 0 0 0-.45-.367c-2.797-1.669-7.15-.398-9.779 1.467m9.676 1.274a.524.524 0 0 1-.11.012m0 0a9.274 9.274 0 0 1-1.814.004" />
                <rect width="3" height="8" x="2" y="14" rx="1.5" />
            </g>
        </svg>`,
    },
    {
      card_title: "Account Transactions",
      card_description:
        "View and manage all your transactions at a glance. Our secure platform allows you to monitor deposits, withdrawals, and transfers, ensuring you have total control over your financial activities.",
      card_link: "/transaction",
      card_svg: `<svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 14 14" {...$$props}>
            <path fill="currentColor" fill-rule="evenodd" d="M1.5 0A1.5 1.5 0 0 0 0 1.5V11a1.5 1.5 0 0 0 1.5 1.5v.702a.75.75 0 0 0 1.5 0V12.5h8v.702a.75.75 0 0 0 1.5 0V12.5A1.5 1.5 0 0 0 14 11V1.5A1.5 1.5 0 0 0 12.5 0zm7.25 4.943c-.721 0-1.306.584-1.307 1.304v.006a1.307 1.307 0 1 0 1.307-1.31M8.124 3.77a2.542 2.542 0 0 0-.687.284l-.587-.587a.625.625 0 0 0-.884.884l.587.587a2.542 2.542 0 0 0-.284.687h-.832a.625.625 0 0 0 0 1.25h.832c.061.245.158.476.284.687l-.587.587a.625.625 0 0 0 .884.884l.587-.587c.211.126.442.223.687.284v.832a.625.625 0 1 0 1.25 0V8.73c.245-.061.476-.158.687-.284l.587.587a.625.625 0 0 0 .884-.884l-.587-.587c.126-.211.223-.442.284-.687h.832a.625.625 0 0 0 0-1.25h-.832a2.544 2.544 0 0 0-.284-.687l.587-.587a.625.625 0 1 0-.884-.884l-.587.587a2.543 2.543 0 0 0-.687-.284v-.832a.625.625 0 1 0-1.25 0zm-5.007.364a.625.625 0 0 0-1.25 0v4.232a.625.625 0 1 0 1.25 0z" clip-rule="evenodd" />
        </svg>`,
    },
  ];
</script>

<div class="container mx-auto px-4">
  <h1 class="text-xl font-semibold text-gray-800 my-4">Welcome to QBank</h1>
  <div class="grid grid-cols-3 gap-4">
    {#each cards as card}
      <DashboardCards {...card} />
    {/each}
  </div>
</div>
