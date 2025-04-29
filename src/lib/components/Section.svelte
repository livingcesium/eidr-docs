<script lang="ts">
    import { fade } from 'svelte/transition';

    /**
     * @prop title – the section heading
     * @prop delay – ms to wait before the fade starts
     * @prop duration – how long the fade lasts
     */
    export let title: string;
    export let delay: number = 0;
    export let duration: number = 500;
    export let className: string = "";
</script>

<section
        in:fade={{ delay, duration }}
        class="relative space-y-2
            transform transition-transform duration-300 hover:scale-105 {className}
            group
        "
>
    <h2
            class="relative z-0 inline-block
             text-2xl font-semibold
             bg-primary text-white
             px-6 py-8 rounded-2xl pt-3"
    >
        {title}
    </h2>

    <!-- Body overlaps the heading, hiding most of it -->
    <div
            class="relative z-10
             bg-gray-600 rounded-2xl overflow-hidden
             -mt-6      /* pull up over heading */
             pt-6       /* push content below heading peek */
             px-3 py-6  /* your slot padding */
             transition-colors duration-300  /* enable color tween */
           group-hover:bg-gray-700       /* target bg on hover-of-parent */
             shadow-lg"
    >
        <slot />
    </div>
</section>