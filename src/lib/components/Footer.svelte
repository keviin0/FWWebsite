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

    let defaultInstagramImageSrc = '/assets/steam_logo_black.svg';
    let hoverInstagramImageSrc = '/assets/steam_logo_white.svg';
    let defaultTiktokImageSrc = '/assets/steam_logo_black.svg';
    let hoverTiktokImageSrc = '/assets/steam_logo_white.svg';
    let defaultTwitterImageSrc = '/assets/steam_logo_black.svg';
    let hoverTwitterImageSrc = '/assets/steam_logo_white.svg';

    let currentInstagramImageSrc = defaultInstagramImageSrc;
    let currentTiktokImageSrc = defaultTiktokImageSrc;
    let currentTwitterImageSrc = defaultTwitterImageSrc;

    function instagram_hover() {
        currentInstagramImageSrc = hoverInstagramImageSrc;
    }

    function instagram_unhover() {
        currentInstagramImageSrc = defaultInstagramImageSrc;
    }

    function tiktok_hover() {
        currentTiktokImageSrc = hoverTiktokImageSrc;
    }

    function tiktok_unhover() {
        currentTiktokImageSrc = defaultTiktokImageSrc;
    }

    function twitter_hover() {
        currentTwitterImageSrc = hoverTwitterImageSrc;
    }

    function twitter_unhover() {
        currentTwitterImageSrc = defaultTwitterImageSrc;
    }
</script>

<div class='footer-container'>
    <div id='s-logo-container'>
        <a href="https://www.instagram.com/freewill_game/" target="_blank"><img class="small-logo" id="instagram-logo" alt="instagram logo" src = {currentInstagramImageSrc} on:mouseover={instagram_hover} on:mouseout={instagram_unhover}/></a>
        <a href="https://www.tiktok.com/@freewillgame" target="_blank"><img class="small-logo" id="tiktok-logo" alt="tiktok logo" src = {currentTiktokImageSrc} on:mouseover={tiktok_hover} on:mouseout={tiktok_unhover}/></a>
        <a href="https://twitter.com/FreeWill_Game" target="_blank"><img class="small-logo" id="twitter-logo" alt="twitter logo" src = {currentTwitterImageSrc} on:mouseover={twitter_hover} on:mouseout={twitter_unhover}/></a>
    </div>
</div>


<style>
    @import "../../styles/About.css";
    @import "../../styles/Footer.css";
</style>