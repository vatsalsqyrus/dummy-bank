<script>
  let fromAccount = "";
  let toAccount = "";
  let amount = "";
  let description = "";
  let errors = {};

  function validateForm() {
    errors = {};
    if (!fromAccount.trim()) errors.fromAccount = "From account is required";
    if (!toAccount.trim()) errors.toAccount = "To account is required";
    if (isNaN(amount) || Number(amount) <= 0)
      errors.amount = "Valid amount is required";
    if (!description.trim()) errors.description = "Description is required";
    return Object.keys(errors).length === 0;
  }

  function handleSubmit() {
    if (validateForm()) {
      // Proceed with form submission logic here, like posting to an API
      console.log("Transferring", {
        fromAccount,
        toAccount,
        amount,
        description,
      });
      alert("Transfer initiated successfully!");
      // Clear the form fields
      fromAccount = "";
      toAccount = "";
      amount = "";
      description = "";
    } else {
      console.log("Errors", errors);
    }
  }
</script>

<div class="container mx-auto px-4 py-4">
  <h1 class="text-lg font-semibold text-gray-800 mb-4">Funds Transfer</h1>
  <form on:submit|preventDefault={handleSubmit} class="space-y-6">
    <div>
      <label class="block text-sm font-medium text-gray-700">From Account</label
      >
      <input
        type="text"
        bind:value={fromAccount}
        id="fromAccount"
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="Your account number"
      />
      {#if errors.fromAccount}
        <p class="mt-2 text-sm text-red-600">{errors.fromAccount}</p>
      {/if}
    </div>
    <div>
      <label class="block text-sm font-medium text-gray-700">To Account</label>
      <input
        type="text"
        bind:value={toAccount}
        id="toAccount"
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="Recipient's account number"
      />
      {#if errors.toAccount}
        <p class="mt-2 text-sm text-red-600">{errors.toAccount}</p>
      {/if}
    </div>
    <div>
      <label class="block text-sm font-medium text-gray-700">Amount</label>
      <input
        type="number"
        bind:value={amount}
        id="amount"
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="Amount in USD"
      />
      {#if errors.amount}
        <p class="mt-2 text-sm text-red-600">{errors.amount}</p>
      {/if}
    </div>
    <div>
      <label class="block text-sm font-medium text-gray-700">Description</label>
      <textarea
        bind:value={description}
        id="description"
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="Why are you transferring the funds?"
      ></textarea>
      {#if errors.description}
        <p class="mt-2 text-sm text-red-600">{errors.description}</p>
      {/if}
    </div>
    <div class="flex items-center justify-between">
      <button
        type="submit"
        id="transfer"
        class="bg-indigo-600 p-4 rounded-md text-white"
      >
        Transfer Funds
      </button>
    </div>
  </form>
</div>
