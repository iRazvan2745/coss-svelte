<script lang="ts">
	import Metadata from "$lib/components/metadata.svelte";
	import { useDesignSystem } from "$lib/features/design-system/index.js";
	import { cn } from "$lib/utils.js";
	import type { PageProps } from "./$types.js";

	let { data }: PageProps = $props();
	const designSystem = useDesignSystem();
</script>

<Metadata
	title={data.meta.name}
	description={data.meta.description}
	ogImage={{
		url: `/og?title=${encodeURIComponent(data.meta.name)}&description=${encodeURIComponent(data.meta.description)}`,
	}}
	ogType="article"
/>

<div
	data-coss-ui
	class={cn(
		"bg-background text-foreground",
		`style-${designSystem.style} base-color-${designSystem.baseColor}`,
		data.meta?.className
	)}
>
	<data.component />
</div>
