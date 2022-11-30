<script>
    export let showModal = false;
    export let isPromo = false;    /*can export in the value of isPromo to override this val*/         
</script>

{#if showModal}
<div class="backdrop" class:promo={isPromo} on:click|self> 
    <div class="modal">
        <slot></slot>
    </div>
</div>
{/if}

<style>
    .backdrop{
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0, 0, 0, 0.8);  /* a is alpha channel to determine how transaprent it is */
    }

    .modal{
        padding: 50px;
        border-radius: 10px;
        max-width: 700px;
        margin: 10% auto;
        text-align: center;
        background: white;
    }

    .promo .modal{
        background: crimson;
        color: white;
    } 
    
</style>