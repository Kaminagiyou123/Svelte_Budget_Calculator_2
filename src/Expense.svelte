<script>
export let name;
export let amount;
let displayButton=false;

const toggle=()=>{
    displayButton=!displayButton
}
</script>
<article class='single-expense'>
    <div class='expense-info'>
<h2>{name} <button class='amount-btn' on:click={toggle}>
    <i class="fas fa-caret-down"></i>
</button></h2>
{#if displayButton} <h4>{amount}</h4>{/if}
</div>
<div class='expense-buttons'>
    <button class='expense-btn edit-btn'><i class='fas fa-pen'></i></button>
    <button class='expense-btn delete-btn'><i class='fas fa-trash'></i></button>
</div>
</article>