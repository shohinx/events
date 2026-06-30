<script lang="ts">
	type EducationData = {
		image: string;
		school: string;
		degree: string;
		graduationYear: string;
	};

	let { data }: { data: EducationData } = $props();
</script>

<div id="educationSection" class="flex w-full flex-col justify-start">
	<div class="text-faint text-xs font-extrabold uppercase">Education</div>
	<div class="mt-4 flex flex-col items-start justify-center">
		<div class="flex w-full">
			<div class="flex shrink-0 flex-col items-center">
				<img src={data.image} alt="{data.school} logo" class="h-12 w-12 shrink-0 rounded-full" />
			</div>
			<div class="ml-3 flex grow flex-col pb-14">
				<div class="flex min-h-12 w-full flex-col sm:flex-row sm:items-center sm:justify-between">
					<div class="flex flex-col items-start justify-start">
						<div class="text-primary text-lg font-semibold sm:text-xl">
							{data.school}
						</div>
						<div class="text-faint -mt-px text-xs">
							{data.degree}
						</div>
					</div>
					<div class="text-tertiary mt-1 flex items-center text-sm sm:mt-0">
						{data.graduationYear}
					</div>
				</div>
			</div>
		</div>
	</div>
</div>
