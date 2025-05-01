<script lang="ts">
    import "bootstrap/dist/css/bootstrap.min.css";
    import { onMount } from "svelte";
    onMount(async () => {
        // @ts-expect-error
        await import("bootstrap/dist/js/bootstrap.bundle.min.js");
    });
</script>

<main class="container mt-3">
    <h1 class="border-bottom mb-3">Demo LUT Generator</h1>
    <slot></slot>
</main>
<footer class="w-100 bg-light text-center p-4">
    &copy; 2025 Hannes Rüger & Laurenz Jaensch<br />
    <i>Built with ❤️, Svelte & Bootstrap - Open Source on <a target="_blank" href="https://github.com/hrueger/demo-lut-generator">GitHub</a></i>
</footer>

<style>
    main {
        min-height: 100vh;
    }
</style>
