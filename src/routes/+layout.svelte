<script lang="ts">
    import "bootstrap/dist/css/bootstrap.min.css";
    import { onMount } from "svelte";
    onMount(async () => {
        // @ts-expect-error
        await import("bootstrap/dist/js/bootstrap.bundle.min.js");
    });
</script>

<div class="container mt-3">
    <h1 class="border-bottom mb-3">Demo LUT Generator</h1>
    <slot></slot>
</div>
