<script>
export let message;
export let showModal = false;
export let isPromo = false;

</script>

{#if showModal}

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- how come there is a comment here that works as coding??? -->
<div class="backdrop" class:promo={isPromo} on:click|self >
  <div class= "modal">
    <slot></slot>
   
    <p>{message}</p>

  </div>
</div>
{/if}

<style>
  .backdrop{
    background-color: rgb(151, 148, 148, 0.5);
    padding: 15px;
    width:50%;
    margin: auto;
    
  }

  .modal{
    background-color: green;
    padding: 10px;
    text-align:center;
  }

  .promo .modal{
    background-color: rgb(229, 108, 128);
    
  }

</style>

