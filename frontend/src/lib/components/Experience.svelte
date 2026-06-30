<script lang="ts">
	type ExperienceItem = {
		company: string;
		role: string;
		duration: string;
		image: string;
	};

	let { data }: { data: ExperienceItem[] } = $props();
</script>

<div id="experienceSection" class="mt-12 flex w-full flex-col justify-start">
	<div class="text-faint text-xs font-extrabold uppercase">Experience</div>
	<div class="mt-6 flex flex-col items-start justify-center">
		{#each data as experience, index (experience.company)}
			<div class="flex w-full">
				<div class="flex shrink-0 flex-col items-center">
					<img
						src={experience.image}
						alt="{experience.company} logo"
						class="h-12 w-12 shrink-0 rounded-full"
					/>
					{#if index !== data.length - 1}
						<div class="bg-background-tertiary w-0.5 grow"></div>
					{/if}
				</div>
				<div class="ml-3 flex grow flex-col pb-14">
					<div class="flex min-h-12 w-full flex-col sm:flex-row sm:items-center sm:justify-between">
						<div class="flex flex-col items-start justify-start">
							<div class="text-primary text-lg font-semibold sm:text-xl">
								{experience.company}
							</div>
							<div class="text-faint text-sm">
								{experience.role}
							</div>
						</div>
						<div class="text-tertiary mt-1 flex items-center text-sm sm:mt-0">
							{#if experience.duration === 'Present'}
								<div
									class="mr-2 h-1.5 w-1.5 animate-pulse rounded-full border-green-700 bg-green-600"
								></div>
							{/if}
							{experience.duration}
						</div>
					</div>
				</div>
			</div>
		{/each}
	</div>
</div>
