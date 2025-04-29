<script>
import { fade } from 'svelte/transition';
import SidebarNav from "$lib/components/SidebarNav.svelte";
</script>


<SidebarNav/>

<div class="content bg-gray-800 w-full text-gray-300">
    <div class="px-80 py-32 text-xl" in:fade={{duration: 500 }}>
        <slot />
    </div>
</div>

<style>
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
    :global(.content table) {
        border-collapse: collapse;
        background-color: #1f2937; /* bg-gray-800 */
        color: #f3f4f6;           /* text-gray-100 */
        border-radius: 0.5rem;
        margin-top: 1rem;
        margin-left: 2rem;
        overflow: hidden;
    }
    :global(.content table tr) {
        transition: background-color 0.3s ease;
    }
    :global(.content table tr:hover) {
        background-color: #101828;
    }
    :global(.content table th) {
        background-color: #374151; /* bg-gray-700 */
        padding: 0.75rem 1rem;
        text-align: left;
        font-weight: 600;
        border-bottom: 1px solid #4b5563; /* border-gray-600 */
    }

    :global(.content table td) {
        padding: 0.75rem 1rem;
        border-bottom: 1px solid #374151; /* border-gray-700 */
    }

    :global(.content table tr:last-child td) {
        border-bottom: none;
    }

    :global(.content hr){
        width: 50%;
        color: #4b5563;
        margin: 4em auto;
    }
</style>