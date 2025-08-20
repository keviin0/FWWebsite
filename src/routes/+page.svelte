<script>
	import './styles.css';
	import { animationDone } from './stores';
    import About from '$lib/components/About.svelte';
	import Trailer from '$lib/components/Trailer.svelte';
	import Credits from '$lib/components/Credits.svelte';
	import Footer from '$lib/components/Footer.svelte';
    import Spacer from '$lib/components/Spacer.svelte';

	let animation;

	animationDone.subscribe((value) => {
		animation = value;
	});
	
</script>


<About/>
<Trailer/>
<Spacer />
<Credits/>
<Spacer />
<Footer/>
<!--
{#if !animation}
	<Intro/>
{:else}
	
{/if}
--->
