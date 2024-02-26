<script>
    import { onMount } from 'svelte';

    onMount(() => {
        const aboutTop = document.getElementById('about-container').getBoundingClientRect().top;
        const scrollTop = document.getElementById('scroll-down').getBoundingClientRect().top;

        setTimeout(() => {
            let elements = document.getElementsByClassName("fade-in");
            Array.from(elements).forEach(element => {
                element.style.opacity = 1;
            });
        }, 500);

        addEventListener("scroll", (event) => { updateScrollOpacity() });

        function updateScrollOpacity() {
            var element = document.getElementById('scroll-down');
            if (!element) return;

            var currentScrollTop = element.getBoundingClientRect().top - window.scrollY;
            var scrolledDistance = scrollTop - currentScrollTop;

            // Ensure we do not divide by zero or get negative values
            var fadeRange = scrollTop - aboutTop;
            if (fadeRange <= 0) return;  // Prevent division by zero or negative ranges

            var opacity = 1 - (scrolledDistance / fadeRange);
            opacity = Math.min(Math.max(opacity, 0), 1); // Clamp opacity between 0 and 1

            console.log(opacity);

            element.style.opacity = opacity;
        }
    });

    

    let logo = '/assets/free_will_logo_glitch_red.png'
    let defaultSteamImageSrc = '/assets/steam_logo_black.svg';
    let hoverSteamImageSrc = '/assets/steam_logo_white.svg';
    let defaultDiscordImageSrc = '/assets/discord_logo_black.svg';
    let hoverDiscordImageSrc = '/assets/discord_logo_red.svg';
    let scrollDown = '/assets/scroll.svg';

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
    <div class='subheader-container fade-in'>
        <span class='subheader-text' id='subheader-date'>May 2024</span>
        <div id='s-logo-container'>
            <a title = "Free Will Steam Page" href="https://store.steampowered.com/app/2571880/Free_Will/" target="_blank"><img class="small-logo" id="steam-logo" alt="steam logo" src = {currentSteamImageSrc} on:mouseover={steam_hover} on:mouseout={steam_unhover}/></a>
            <a title = "Free Will Community Discord" href="https://discord.gg/umAuPM9KCJ" target="_blank"><img class="small-logo" id="discord-logo" alt="discord logo" src = {currentDiscordImageSrc} on:mouseover={discord_hover} on:mouseout={discord_unhover}/>
        </div>
    </div>

    <img class='fade-in' id='scroll-down' alt="scroll down"src={scrollDown}/>
</div>


<style>
    @import "../../styles/About.css";
</style>