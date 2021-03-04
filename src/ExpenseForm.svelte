<script>
    import Title from './Title.svelte'
    let name=''
    let amount=null
    export let addExpense;
    $: isEmpty=!name ||! amount

    const handleSubmit=()=>{
        addExpense({name,amount})
        name=''
        amount=null
    }
</script>

<section class='form'>
<Title title='add expense'/>
<form class='expense-form' on:submit|preventDefault={handleSubmit}>
    <div class='form-control'>
        <lable for='name'>name</lable>
        <input type='text' id='name' bind:value={name}/>
    </div>
    <div class='form-control'>
        <lable for='amount' >amount</lable>
        <input type='number' id='amount' bind:value={amount}/>
    </div>
    {#if isEmpty}
    <p class='form-empty'> please fill out all form fields</p>
    {/if}
    <button type='submit' class='btn btn-block'> add expense</button>

    <button type='submit' class='close-btn'> 
        <i class='fas fa-times'/> close
    </button>
</form>


</section>