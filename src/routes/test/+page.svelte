<script lang="ts">
	import * as RadioGroup from '$lib/components/ui/radio-group';
	import { Label } from '$lib/components/ui/label';
	import { Button } from '$lib/components/ui/button';
	let order = $state('flex-col');
</script>

<div class="flex flex-col gap-y-4">
	<h1 class="text-4xl">are you a gay?</h1>
	<RadioGroup.Root value="gay" class={`flex ${order}`}>
		<div class="flex items-center space-x-2">
			<RadioGroup.Item value="gay" id="r1" tabindex={-1} />
			<Label for="r1">yes</Label>
		</div>
		<div
			class="flex items-center space-x-2"
			onmouseover={() => {
				order = order === 'flex-col' ? 'flex-col-reverse' : 'flex-col';
			}}
		>
			<RadioGroup.Item value="not-gay" id="r2" tabindex={-1} />
			<Label for="r2">no</Label>
		</div>
	</RadioGroup.Root>
	<Button href="/result">show result</Button>
</div>
