<script>
    import { onMount } from 'svelte';

    onMount(() => {
        setTimeout(() => {
            let elements = document.getElementsByClassName("subheader-container");
            Array.from(elements).forEach(element => {
                element.style.opacity = 1;
            });
        }, 500);
    });
    let logo = '/assets/free_will_logo_glitch_red.png'
    let defaultSteamImageSrc = '/assets/steam_logo_black.svg';
    let hoverSteamImageSrc = '/assets/steam_logo_white.svg';
    let defaultDiscordImageSrc = '/assets/discord_logo_black.svg';
    let hoverDiscordImageSrc = '/assets/discord_logo_red.svg';

    let currentSteamImageSrc = defaultSteamImageSrc;
    let currentDiscordImageSrc = defaultDiscordImageSrc;

    function steam_hover() {
        currentSteamImageSrc = hoverSteamImageSrc;
    }

    function steam_unhover() {
        currentSteamImageSrc = defaultSteamImageSrc;
    }

    function discord_hover() {
        currentDiscordImageSrc = hoverDiscordImageSrc;
    }

    function discord_unhover() {
        currentDiscordImageSrc = defaultDiscordImageSrc;
    }
</script>

<div id="about-container">
    <img id='logo' alt='Free Will Logo' src={logo}> 
    <div class='subheader-container'>
        <span class='subheader-text' id='subheader-date'>May 2024</span>
        <div id='s-logo-container'>
            <a href="https://store.steampowered.com/app/2571880/Free_Will/" target="_blank"><img class="small-logo" id="steam-logo" alt="steam logo" src = {currentSteamImageSrc} on:mouseover={steam_hover} on:mouseout={steam_unhover}/></a>
            <a href="https://discord.gg/umAuPM9KCJ" target="_blank"><img class="small-logo" id="discord-logo" alt="steam logo" src = {currentDiscordImageSrc} on:mouseover={discord_hover} on:mouseout={discord_unhover}/>
        </div>
    </div>
</div>


<style>
    @import "../../styles/About.css";
</style>