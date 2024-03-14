<script>
	import './styles.css';
	import { inject } from '@vercel/analytics';
	import { dev } from '$app/environment';
	import Intro from '../lib/components/Intro.svelte';
	import { animationDone } from './stores';
    import Spacer from '$lib/components/Spacer.svelte';
    import About from '$lib/components/About.svelte';
	import Trailer from '$lib/components/Trailer.svelte';
	import Credits from '$lib/components/Credits.svelte';
	import Footer from '$lib/components/Footer.svelte';

	let animation;

	animationDone.subscribe((value) => {
		animation = value;
	});
	
	inject({ mode: dev ? 'development' : 'production' });
</script>

<!-- <Intro /> -->
<About/>
<Trailer/>
<Spacer />
<Credits/>
<Spacer />
<Footer/>
<slot />

<style>
</style>
