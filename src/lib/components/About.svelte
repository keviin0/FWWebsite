<script>
	import logo from '$lib/assets/free_will_logo_glitch_red.png';
    import { onMount } from 'svelte';

    onMount(() => {
        setTimeout(() => {
            document.getElementById("subheader").style.opacity = 1;
        }, 10);
    });
</script>

<span id="logo-container">
    <img id='logo' alt='Free Will Logo' src={logo}> 
    <span class='regular-text' id='subheader'>Available May 2024</span>
</span>

<style>
    @import "../../styles/About.css";
</style>