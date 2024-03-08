<script lang="ts">
	import { cn } from '$lib/utils';
	import { Motion } from 'svelte-motion';
	export let className: string | undefined = undefined;
	export let containerClassName: string | undefined = undefined;
	export let animate = true;
	const variants = {
		initial: {
			backgroundPosition: '0 50%'
		},
		animate: {
			backgroundPosition: ['0, 50%', '100% 50%', '0 50%']
		}
	};
</script>

<div class={cn('group relative p-[4px]', containerClassName)}>
	<Motion
		let:motion
		variants={animate ? variants : undefined}
		initial={animate ? 'initial' : undefined}
		animate={animate ? 'animate' : undefined}
		transition={animate
			? {
					duration: 5,
					repeat: Infinity,
					repeatType: 'reverse'
				}
			: undefined}
		style={{
			backgroundSize: animate ? '400% 400%' : undefined
		}}
	>
		<div
			use:motion
			class={cn(
				'absolute inset-0 z-[1] opacity-60 blur-xl transition  duration-500 group-hover:opacity-100',
				'bg-gradient-to-r from-red-500 via-green-500 to-violet-500'
			)}
		/>
	</Motion>

	<Motion
		let:motion
		variants={animate ? variants : undefined}
		initial={animate ? 'initial' : undefined}
		animate={animate ? 'animate' : undefined}
		transition={animate
			? {
					duration: 5,
					repeat: Infinity,
					repeatType: 'reverse'
				}
			: undefined}
		style={{
			backgroundSize: animate ? '400% 400%' : undefined
		}}
	>
		<div
			use:motion
			class={cn(
				'absolute inset-0 z-[1]',
				'bg-gradient-to-r from-red-500 via-green-500 to-violet-500'
			)}
		/>
	</Motion>

	<div class={cn('relative z-10', className)}><slot /></div>
</div>
