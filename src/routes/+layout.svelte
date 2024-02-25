<script>
	import './styles.css';
	import { inject } from '@vercel/analytics'
	import Intro from '../lib/components/Intro/Intro.svelte';
	import { animationDone } from './stores';
    import About from '$lib/components/About.svelte';

	let animation;

	animationDone.subscribe((value) => {
		animation = value;
	});
	
</script>

{#if !animation}
	<Intro/>
{:else}
	<About/>
  	<slot />
{/if}