<script>
	import './styles.css';
	import { inject } from '@vercel/analytics';
	import { dev } from '$app/environment';
	import Intro from '../lib/components/Intro/Intro.svelte';
	import { animationDone } from './stores';
	import About from '$lib/components/About.svelte';
	import Footer from '$lib/components/Footer.svelte';

	let animation;

	animationDone.subscribe((value) => {
	animation = value;
	});

	inject({ mode: dev ? 'development' : 'production' });
</script>

{#if !animation}
<Intro/>
{:else}
<About/>
<slot />
<Footer/>
{/if}