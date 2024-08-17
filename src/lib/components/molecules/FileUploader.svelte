<script lang="ts">
    import Plot from 'svelte-plotly.js';

    // props
    export let data: Array<{ x: number[], y: number[], type: string }> = [];

    // Function to handle file upload
    function handleFileUpload(event: Event) {
        const input = event.target as HTMLInputElement;
        if (input.files && input.files.length > 0) {
            const file = input.files[0];
            const reader = new FileReader();
            reader.onload = () => {
                const text = reader.result as string;
                const parsedData = parseCSV(text);
                data = parsedData;
            };
            reader.readAsText(file);
        }
    }

    // Function to parse CSV data
    function parseCSV(text: string): Array<{ x: number[], y: number[], type: string }> {
        const rows = text.split('\n').map(row => row.split(',').map(Number));
        const x = rows.map(row => row[0]);
        const y = rows.map(row => row[1]);
        return [{ x, y, type: 'scatter' }];
    }
</script>

<div>
    input(type="file" accept=".csv" on:change={handleFileUpload})
    Plot({ data } layout = { margin: { t: 0 } } fillParent="width" debounce = 250)
</div>