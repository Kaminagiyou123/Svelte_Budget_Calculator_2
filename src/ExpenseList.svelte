<script>
import Title from './Title.svelte'
export let total;
export let expenseData;
import Expense from './Expense.svelte'

</script>
<section>
<Title title={'expense list'}/>
<Title title={`Total Expense: ${total}`}/>
<ul>
{#each expenseData as expense}
<li><Expense {...expense}/></li>
{/each}
</ul>
</section>