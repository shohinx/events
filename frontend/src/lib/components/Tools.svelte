<script lang="ts">
	type BadgeItem = {
		icon: string;
		text: string;
	};

	let { data }: { data: BadgeItem[] } = $props();
</script>

<div id="toolsSection" class="mt-6 flex w-full flex-col justify-start">
	<div class="text-faint text-xs font-extrabold uppercase">Tools</div>
	<div class="mt-4 flex flex-wrap gap-1.5">
		{#each data as tool (tool.text)}
			<div
				class="text-tertiary bg-background-tertiary border-background-secondary flex items-center justify-center space-x-1.25 rounded-md border px-1.5 py-1 text-xs font-medium"
			>
				<!-- eslint-disable-next-line svelte/no-at-html-tags -- Icons are trusted inline SVG strings from +page.svelte. -->
				{@html tool.icon}
				<div>{tool.text}</div>
			</div>
		{/each}
	</div>
</div>
