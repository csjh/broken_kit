<script lang="ts" context="module">
    import * as echarts from "echarts/core.js";
    import { GridComponent } from "echarts/components.js";
    import { LineChart } from "echarts/charts.js";
    import { UniversalTransition } from "echarts/features.js";
    import { CanvasRenderer } from "echarts/renderers.js";

    import type { EChartsOption } from "echarts";
    import { onMount } from "svelte";

    echarts.use([GridComponent, LineChart, CanvasRenderer, UniversalTransition]);
</script>

<script lang="ts">
    const options: EChartsOption = {
        xAxis: {
            type: "category" as const,
            data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
        },
        yAxis: {
            type: "value" as const
        },
        series: [
            {
                data: [150, 230, 224, 218, 135, 147, 260],
                type: "line" as const
            }
        ]
    };

    let element: HTMLDivElement;

    onMount(() => {
        const echartsInstance = echarts.init(element, "dark", {
            renderer: "canvas"
        });
        echartsInstance.setOption(options);
    });
</script>

<div class="chart" bind:this={element} />

<style>
    .chart {
        width: 100%;
        height: 20em;
        margin: auto;
        padding-top: 20px;
        overflow: visible;
        display: flex;
        margin-bottom: 1.5em;
    }
</style>