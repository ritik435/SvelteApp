<script>
    export let toShow = false;
    export let isPromo = false;
</script>

{#if toShow}
    <div class="backdrop" class:promo={isPromo} on:click|self>
        <div class="modal">
            <slot />
        </div>
    </div>
{/if}
<main />

<style>
    .backdrop {
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0, 0, 0, 0.8);
    }
    .modal {
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 10% auto;
        text-align: center;
        background: white;
    }
    .promo .modal {
        background: rgba(218, 62, 62, 0.8);
        color: whitesmoke;
    }
</style>
