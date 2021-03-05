<script>
	import Navbar from './Navbar.svelte'
	import ExpenseList from './ExpenseList.svelte'
	import expenses from './expenses'
	import { setContext } from 'svelte';
	import ExpenseForm from './ExpenseForm.svelte'

	let total;
	let expenseData=[...expenses]

	let setName='';
	let setAmount=null;
	let setId=null;
	let isFormOpen=false;



$:total=  expenseData.map((item)=>item.amount).reduce((accumulator, currentValue) => accumulator + currentValue,0 )
$: isEditing= setId?true:false

const openForm=()=>{
	isFormOpen=true
}


const closeForm=()=>{
	isFormOpen=false
}
const deleteExpense=(id)=>{expenseData=expenseData.filter((expense)=>expense.id!==id)}
const clearExpenses=()=>{expenseData=[]}

const addExpense=({name,amount})=>{
	let newExpense={
		id: Math.random() * Date.now(),
		name:name,
		amount:amount
	}
	expenseData=[newExpense,...expenses]
	name=''
	amount=null
}

const editExpense=({name,amount})=>{
	expenseData=expenseData.map((expense)=>{
		if (expense.id===setId){ return {...expense,name,amount}}
		else {return {...expense}}
	})
	name=''
	amount=null
}

const setModifiedExpense=(id)=>{
	let expense=expenses.find(item=> item.id===id)
	setId=expense.id
	setAmount=expense.amount
	setName=expense.name

}

setContext('deleteExpense', deleteExpense);
setContext('setModifiedExpense',setModifiedExpense)

 </script>

<Navbar {openForm}/>

<main class='content'>
{#if isFormOpen}
	<ExpenseForm addExpense={addExpense} editExpense={editExpense}
name={setName} amount={setAmount} id={setId} isEditing={isEditing} {closeForm}/>
{/if}

<ExpenseList expenseData={expenseData} total={total}/>
<button type='button' class='btn btn-primary btn-block'
on:click={clearExpenses}
>clear expenses</button>

</main>