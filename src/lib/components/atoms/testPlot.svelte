<script lang="ts">
	import { list } from 'postcss';
    import Plot from 'svelte-plotly.js';

    // props
    export let data = Object[] = [];
</script>

<template lang="pug">
    Plot(
        { data },
        layout = {
            margin: { t: 0 }
        },
        fillParent="width",
        debounce = {250}
    )
</template>