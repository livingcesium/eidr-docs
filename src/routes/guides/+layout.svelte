<script>

import SidebarNav from "$lib/components/SidebarNav.svelte";
</script>


<SidebarNav/>

<div class="content bg-gray-800 w-full text-gray-300">
    <div class="px-80 py-32 text-xl">
        <slot />
    </div>
</div>

<style>
    /* now all these only apply inside `.content` */

    :global(.content code) {
        color: #fff;
        padding: 4px;
        background-color: #101828;
    }

    :global(.content pre > code) {
        display: block;
        margin: 0;
        border-radius: 5px;
        max-width: fit-content;
        white-space: pre-wrap;
    }

    :global(.content h2 + pre > code),
    :global(.content h2 ~ pre > code) {
        display: inline-block;
        margin: 2rem auto;
        padding: 2rem;
    }

    :global(.content h1) {
        font-size: 2em;
        margin-bottom: 0.75em;
    }

    :global(.content h2) {
        font-size: 1.5em;
        margin-bottom: 0.5em;
    }

    :global(.content h3) {
        margin-top: 3em;
        margin-bottom: 0.5em;
    }

    :global(.content li) {
        margin-left: 2em;
    }

    :global(.content p) {
        margin-top: 0.75em;
    }
</style>