<script>
	import Navbar from './Navbar.svelte'
	import ExpenseList from './ExpenseList.svelte'
	import expenses from './expenses'
	import { setContext } from 'svelte';
	let total;
	let expenseData=[...expenses]

$:total=  expenseData.map((item)=>item.amount).reduce((accumulator, currentValue) => accumulator + currentValue,0 )


const deleteExpense=(id)=>{expenseData=expenseData.filter((expense)=>expense.id!==id)}
const clearExpenses=()=>{expenseData=[]}

setContext('deleteExpense', deleteExpense);

 </script>


<Navbar/>
<main class='content'>
<ExpenseList expenseData={expenseData} total={total}/>
<button type='button' class='btn btn-primary btn-block'
on:click={clearExpenses}
>clear expenses</button>

</main>