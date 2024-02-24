<script>
	import './styles.css';
	import Intro from '../lib/components/Intro/Intro.svelte';
	import { animationDone } from './stores';

	let animation;

	animationDone.subscribe((value) => {
		animation = value;
	});
</script>

{#if !animation}
  <Intro/>
{:else}
  
  <slot />
{/if}
