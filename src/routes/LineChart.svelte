<script lang="ts">
    import { onMount } from "svelte";
    import { Chart, LineController, LineElement, PointElement, LinearScale, Title, Tooltip, CategoryScale, type ChartDataset } from "chart.js";

    let canvas: HTMLCanvasElement;

    let { datasets }: { datasets: ChartDataset<"line">[] } = $props();

    Chart.register(LineController, LineElement, PointElement, LinearScale, Title, Tooltip, CategoryScale);

    $effect(() => {
        if (!chart) return;
        chart.data.datasets = datasets;
        chart.update();
    });

    let chart: Chart | null = null;
    onMount(() => {
        const ctx = canvas.getContext("2d")!;
        chart = new Chart(ctx, {
            type: "line",
            data: {
                datasets,
            },
            options: {
                animation: false,
                maintainAspectRatio: false,
                scales: {
                    x: {
                        type: "linear",
                        min: 0,
                        max: 1,
                        title: {
                            display: true,
                            text: "Input",
                        },
                    },
                    y: {
                        type: "linear",
                        min: 0,
                        max: 1,
                        title: {
                            display: true,
                            text: "Output",
                        },
                    },
                },
            },
        });
    });
</script>

<div class="ratio ratio-1x1">
    <canvas bind:this={canvas}></canvas>
</div>
