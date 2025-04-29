<script lang="ts">
    /**
     * A flex‐centered full‐screen container.
     * Accepts extra classes via `className` prop.
     */
    export let className = "";
    export let expand = false;
</script>

<div
        class={`container mx-auto px-4 flex flex-col items-center justify-center min-h-screen
        ${expand
          ? 'w-full max-w-none'  /* no max-width, will grow with children */
          : 'container'          /* Tailwind’s default container */
        }
        ${className}`}
>
    <slot />
</div>
