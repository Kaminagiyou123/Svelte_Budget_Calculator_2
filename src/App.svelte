<script>
	import Navbar from './Navbar.svelte'
	import ExpenseList from './ExpenseList.svelte'
	import expenses from './expenses'
	let total;
$:total= expenses.map((expense)=>expense.amount).reduce( (accumulator, currentValue) => accumulator + currentValue )
 </script>


<Navbar/>
<main class='content'>
<ExpenseList expenses={[...expenses]} total={total}/>

</main>