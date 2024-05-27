<script>
  import { page } from "$app/stores";
  import Backbutton from "../../../../components/Backbutton.svelte";
  let loan_type = $page.params.slug;
  let loanTitle = {};
  let name = "";
  let email = "";
  let amount = "";
  let term = "";
  let interestRate = 0;
  let errors = {};
  $: success_message = "";

  const interestRates = {
    home: { min: 7, max: 9 },
    personal: { min: 12, max: 24 },
    education: { min: 14, max: 18 },
    car: { min: 12, max: 19 },
    business: { min: 8, max: 15 },
  };
  $: {
    loanTitle =
      {
        home: "Home Loan",
        personal: "Personal Loan",
        education: "Education Loan",
        car: "Car Loan",
        business: "Business Loan",
      }[loan_type] || "Loan Application";

    if (interestRates[loan_type]) {
      const { min, max } = interestRates[loan_type];
      interestRate = (Math.random() * (max - min) + min).toFixed(2);
    }
  }

  function validateForm() {
    errors = {};
    if (!name.trim()) errors.name = "Name is required";
    if (!email.trim() || !email.includes("@"))
      errors.email = "Valid email is required";
    if (isNaN(amount) || Number(amount) <= 0 || Number(amount) > 1000000)
      errors.amount = "Valid loan amount is required. Cannot exceed 1000000.";
    if (isNaN(term) || Number(term) <= 0 || Number(term) > 5)
      errors.term = "Loan term must be a positive number and maximum should be 5 years.";
    return Object.keys(errors).length === 0;
  }

  function handleSubmit() {
    if (validateForm()) {
      // Proceed with form submission logic here, like posting to an API
      //   console.log("Submitting", { name, email, amount, term, interestRate });
      success_message = `${loanTitle} Application Successful`;
      console.log(success_message)
    } else {
      console.log("Errors", errors);
    }
  }
</script>

<div class="container mx-auto px-4">
    <Backbutton />
  <h1 class="text-xl font-semibold text-gray-800 my-4">
    {loanTitle} Application
  </h1>
  <h2 class="text-md text-gray-600">Interest Rate: {interestRate}%</h2>
  <form on:submit|preventDefault={handleSubmit} class="space-y-6">
    <div>
      <label class="block text-sm font-medium text-gray-700">Name</label>
      <input
        type="text"
        bind:value={name}
        id="name"
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
        id="email"
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
        id="loanAmount"
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
        id="term"
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
        id="apply"
        class="bg-indigo-600 p-4 rounded-md text-white"
        on:click={handleSubmit}
      >
        Apply for {loanTitle}
      </button>
      {#if success_message.length > 0}
        <span class="text-green-500 text-md">{success_message}</span>
      {/if}
    </div>
  </form>
</div>
