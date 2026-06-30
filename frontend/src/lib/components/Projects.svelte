<script lang="ts">
	import { ExternalLinkIcon } from 'lucide-svelte';

	type UmamiTracker = {
		track: (eventName: string, data?: Record<string, string>) => void | Promise<unknown>;
	};

	type UmamiWindow = Window & {
		umami?: UmamiTracker;
	};

	type ProjectItem = {
		name: string;
		technology: string;
		description: string;
		link: string;
	};

	let { data }: { data: ProjectItem[] } = $props();

	function trackProjectLink(project: ProjectItem) {
		try {
			void (window as UmamiWindow).umami?.track(`Project link: ${project.name}`, {
				project: project.name,
				technology: project.technology,
				description: `${project.name} project link clicked: ${project.link}`,
				url: project.link
			});
		} catch {
			// Never let analytics block navigation.
		}
	}
</script>

<div id="projectsSection" class="mt-12 flex w-full flex-col justify-start">
	<div class="text-faint text-xs font-extrabold uppercase">Personal projects</div>
	<div class="mt-6 grid grid-cols-1 items-start justify-center gap-6 sm:grid-cols-2">
		{#each data as project (project.name)}
			<div
				class="from-background-secondary to-background border-background-tertiary flex flex-col rounded-md border bg-radial p-4"
			>
				<div class="mt-4 flex h-full flex-col">
					<div class="flex items-center justify-between">
						<div class="text-primary flex items-center text-xl font-medium">
							{project.name}
							<a
								href={project.link}
								target="_blank"
								rel="external noopener noreferrer"
								onclick={() => trackProjectLink(project)}
								class="hover:bg-faint/20 text-secondary m-1 flex cursor-pointer items-center rounded-md p-1 text-xs transition"
							>
								<ExternalLinkIcon class="h-3.5 w-3.5" strokeWidth={1.5} />
							</a>
						</div>
						<div class="text-faint text-xs font-medium">
							{project.technology}
						</div>
					</div>
					<div class="text-secondary mt-4 mb-2 text-sm">
						{project.description}
					</div>
				</div>
			</div>
		{/each}
	</div>
</div>
