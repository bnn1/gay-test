<script lang="ts">
	import BackgroundGradient from '$lib/components/ui/background-gradient/background-gradient.svelte';
	import { Skeleton } from '$lib/components/ui/skeleton';
	import { Confetti } from 'svelte-confetti';
	let hover = $state(false);

	function changeHover(newHover: boolean) {
		hover = newHover;
	}
</script>

<div
	style="position: fixed; top: -50px; left: 0; height: 100vh; width: 100vw; display: flex; justify-content: center; overflow: hidden;"
>
	<Confetti
		x={[-5, 5]}
		y={[0, 0.1]}
		delay={[500, 2000]}
		infinite
		duration={5000}
		amount={200}
		fallDistance="100vh"
	/>
</div>
<div class="h-screen w-screen">
    <BackgroundGradient className='w-full h-full' containerClassName='w-full h-full flex-1 rounded-none'>
    	<div class="flex flex-col gap-y-4 justify-center items-center h-full">
    	    <h1 class="text-2xl">congrats! you're a gay</h1>
        	{#if hover}
        		<p onmouseleave={() => changeHover(false)}>me too</p>
        	{:else}
        		<Skeleton class="h-6 w-20" onmouseover={() => changeHover(true)} />
        	{/if}
    	</div>
    </BackgroundGradient>
    
</div>