<script>
  import Backbutton from "../../../components/Backbutton.svelte";

  let loanTitle = {};
  let name = "";
  let email = "";
  let amount = "";
  let term = "";
  let errors = {};

  $: {
    loanTitle =
      {
        home: "Home Loan Application",
        personal: "Personal Loan Application",
        education: "Education Loan Application",
      } || "Loan Application";
  }

  function validateForm() {
    errors = {};
    if (!name.trim()) errors.name = "Name is required";
    if (!email.trim() || !email.includes("@"))
      errors.email = "Valid email is required";
    if (!amount.trim() || isNaN(amount) || Number(amount) <= 0)
      errors.amount = "Valid loan amount is required";
    if (!term.trim() || isNaN(term) || Number(term) <= 0)
      errors.term = "Loan term must be a positive number";
    return Object.keys(errors).length === 0;
  }

  function handleSubmit() {
    if (validateForm()) {
      // Proceed with form submission logic here, like posting to an API
      console.log("Submitting", { name, email, amount, term });
    } else {
      console.log("Errors", errors);
    }
  }
</script>

<div class="container mx-auto px-4">
  <Backbutton />
  <h1 class="text-xl font-semibold text-gray-800 my-4">Loan Application</h1>
  <form on:submit|preventDefault={handleSubmit} class="space-y-6">
    <div>
      <label class="block text-sm font-medium text-gray-700">Name</label>
      <input
        type="text"
        bind:value={name}
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="Your full name"
      />
      {#if errors.name}
        <p class="mt-2 text-sm text-red-600">{errors.name}</p>
      {/if}
    </div>
    <div>
      <label class="block text-sm font-medium text-gray-700"
        >Email Address</label
      >
      <input
        type="email"
        bind:value={email}
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="you@example.com"
      />
      {#if errors.email}
        <p class="mt-2 text-sm text-red-600">{errors.email}</p>
      {/if}
    </div>
    <div>
      <label class="block text-sm font-medium text-gray-700">Loan Amount</label>
      <input
        type="number"
        bind:value={amount}
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="Amount in USD"
      />
      {#if errors.amount}
        <p class="mt-2 text-sm text-red-600">{errors.amount}</p>
      {/if}
    </div>
    <div>
      <label class="block text-sm font-medium text-gray-700"
        >Term (in years)</label
      >
      <input
        type="number"
        bind:value={term}
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="Number of years"
      />
      {#if errors.term}
        <p class="mt-2 text-sm text-red-600">{errors.term}</p>
      {/if}
    </div>
    <div class="flex items-center justify-between">
      <button
        type="submit"
        class="w-full flex justify-center py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
      >
        Apply for Loan
      </button>
    </div>
  </form>
</div>
