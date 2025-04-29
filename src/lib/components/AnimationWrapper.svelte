<script lang="ts">
    import { fade } from 'svelte/transition';
    import { onMount } from 'svelte';

    // true only after the browser has mounted
    let mounted = false;
    onMount(() => (mounted = true));
</script>

{#if mounted}
    <div>
        <slot />
    </div>
{/if}