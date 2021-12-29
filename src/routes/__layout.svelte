<script lang="ts">
    import Header from '$lib/header/index.svelte';
</script>
<main>
</main>
<Header />
<style>
    :global(*) {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    :global(.container) {
        width: 100%;
        height: 100%;
    }

    :global(.relative){
        position: relative;
    }

    :global(.absolute){
        position: absolute;
    }
</style>
