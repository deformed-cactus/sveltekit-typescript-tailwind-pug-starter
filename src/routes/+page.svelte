<!-- Example Svelte Page / Starter Web Page-->
<script lang="ts">
	// components
	import FileUploader from "$molecules/FileUploader.svelte";
	 
</script>

<template lang="pug">
	//- head
	svelte:head
		title The Quotient Group
		meta(
			content="Welcome. We hope you find our tools useful.",
			name="The Quotient Group"
		)

	//- body
	main
		div
			FileUploader()
			

	 
</template>
