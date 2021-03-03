<script>
import Title from './Title.svelte'
export let total;
export let expenses;
import Expense from './Expense.svelte'

</script>
<section>
<Title title={'expense list'}/>
<Title title={`Total Expense: ${total}`}/>
<ul>
{#each expenses as expense}
<li><Expense {...expense}/></li>
{/each}
</ul>
</section>