<!-- https://svelte.dev/docs/introduction -->

<!-- https://svelte.dev/docs/special-elements -->

<!-- JavaScript -->
<script>
  export let showModal2 = false; //Will show 'modal' if set to 'true'
  export let isPromo = false; //Will add a class of 'promo' if set to 'true'
</script>


<!-- HTML -->
 {#if showModal2}
    <!-- onClick will pick up from props passed in. -->
    <!-- self means ONLY itself when clicked on. -->
    <div class="backdrop" class:promo={isPromo} on:click|self>
        <div class="modal">
            <slot></slot>
            <slot name="title">
                <!-- will look for a slot with name of 'title' and output it here -->
            </slot>
        </div>
    </div>
{/if}

<!-- CSS -->
<style>
    /** Only applies to THIS file */
    .backdrop {
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0,0,0,0.5)
    }
	.modal {
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 10% auto;
        text-align: center;
        background: rgb(32, 235, 32);
    }

    .promo .modal{
        background: rgb(20, 220, 37);
        color: white;
    }
</style>