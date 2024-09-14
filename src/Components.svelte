<!-- https://svelte.dev/docs/introduction -->

<!-- https://svelte.dev/docs/svelte-components -->
 <!-- https://svelte.dev/examples/event-modifiers -->
<!-- JavaScript -->
<script>
  export let message = "default value"; //The prop that gets passed in from "App.svelte" (will change when data comes in)
  export let showModal = false; //Will show 'modal' if set to 'true'
  export let isPromo = false; //Will add a class of 'promo' if set to 'true'
</script>


<!-- HTML -->
 {#if showModal}
    <!-- onClick will pick up from props passed in. -->
    <!-- self means ONLY itself when clicked on. -->
    <div class="backdrop" class:promo={isPromo} on:click|self>
        <div class="modal">
            <p>Sign up for offers!</p>
            <p>-----</p>
            <super>{message}</super>
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
        background: white;
    }

    .promo .modal{
        background: crimson;
        color: white;
    }
</style>