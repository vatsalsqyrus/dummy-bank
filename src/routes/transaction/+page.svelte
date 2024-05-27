<script>
  import Backbutton from "../../components/Backbutton.svelte";
  import Transfer from "../../components/Transfer.svelte";
  // Dummy transaction data
  const transactions = [
    {
      date: "2024-05-01",
      description: "ATM Withdrawal",
      type: "Debit",
      amount: "-$200.00",
      balance: "$800.00",
    },
    {
      date: "2024-05-02",
      description: "Direct Deposit - Paycheck",
      type: "Credit",
      amount: "+$2,500.00",
      balance: "$3,300.00",
    },
    {
      date: "2024-05-05",
      description: "Grocery Store",
      type: "Debit",
      amount: "-$150.00",
      balance: "$3,150.00",
    },
    {
      date: "2024-05-10",
      description: "Utility Bill",
      type: "Debit",
      amount: "-$120.00",
      balance: "$3,030.00",
    },
    {
      date: "2024-05-15",
      description: "Online Transfer to Savings",
      type: "Debit",
      amount: "-$500.00",
      balance: "$2,530.00",
    },
    {
      date: "2024-05-20",
      description: "Received Transfer",
      type: "Credit",
      amount: "+$150.00",
      balance: "$2,680.00",
    },
    {
      date: "2024-05-25",
      description: "Restaurant",
      type: "Debit",
      amount: "-$75.00",
      balance: "$2,605.00",
    },
  ];
</script>

<div class="container mx-auto px-4 py-4">
  <Backbutton />
  <h1 class="text-lg font-semibold text-gray-800 mb-4">Account Transactions</h1>
  <table class="min-w-full bg-white">
    <thead class="bg-gray-800 text-white">
      <tr>
        <th class="w-1/4 px-4 py-2">Date</th>
        <th class="w-1/4 px-4 py-2">Description</th>
        <th class="w-1/4 px-4 py-2">Type</th>
        <th class="w-1/4 px-4 py-2">Amount</th>
        <th class="w-1/4 px-4 py-2">Balance</th>
      </tr>
    </thead>
    <tbody class="text-gray-700">
      {#each transactions as transaction}
        <tr>
          <td class="border px-4 py-2">{transaction.date}</td>
          <td class="border px-4 py-2">{transaction.description}</td>
          <td class="border px-4 py-2">{transaction.type}</td>
          <td
            class={transaction.amount.startsWith("+")
              ? "border px-4 py-2 text-green-500"
              : "border px-4 py-2 text-red-500"}>{transaction.amount}</td
          >
          <td class="border px-4 py-2">{transaction.balance}</td>
        </tr>
      {/each}
    </tbody>
  </table>
  <div class="mt-4">
    <Transfer />
  </div>
</div>
