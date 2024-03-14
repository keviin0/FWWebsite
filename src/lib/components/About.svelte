<script>
  import { onMount } from "svelte";

  const clamp = (num, min, max) => Math.min(Math.max(num, min), max);

  onMount(() => {
    const adjustedHeight = window.innerHeight / 1.5;
    const denominator =
      document.getElementById("scroll-down").getBoundingClientRect().top -
      adjustedHeight;
    const logo = document.getElementById("logo");
    logo.style.opacity = 1;

    setTimeout(() => {
      let elements = document.getElementsByClassName("fade-in");
      Array.from(elements).forEach((element) => {
        element.style.opacity = 1;
      });
    }, 200);

    addEventListener("scroll", (event) => {
      updateScrollOpacity();
    });

    function updateScrollOpacity() {
      var element = document.getElementById("scroll-down");
      if (!element) return;

      document.getElementById("scroll-down").style.transition =
        "opacity 0.7s ease-in-out";

      var newOpacity = clamp(
        (element.getBoundingClientRect().top - adjustedHeight) / denominator,
        0,
        1
      );
      element.style.opacity = newOpacity;
    }
  });

  let logo = "/assets/free_will_logo_glitch_red.png";
  let defaultSteamImageSrc = "/assets/steam_logo_black.svg";
  let hoverSteamImageSrc = "/assets/steam_logo_white.svg";
  let defaultDiscordImageSrc = "/assets/discord_logo_black.svg";
  let hoverDiscordImageSrc = "/assets/discord_logo_red.svg";
  let scrollDown = "/assets/scroll.svg";

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
  <img id="logo" alt="Free Will Logo" src={logo} />
  <div class="subheader-container fade-in">
    <span class="subheader-text" id="subheader-date">May 2024</span>
    <div id="s-logo-container">
      <a
        title="Free Will Steam Page"
        href="https://store.steampowered.com/app/2571880/Free_Will/"
        target="_blank"
        ><img
          class="small-logo"
          id="steam-logo"
          alt="steam logo"
          src={currentSteamImageSrc}
          on:mouseover={steam_hover}
          on:mouseout={steam_unhover} /></a>
      <a
        title="Free Will Community Discord"
        href="https://discord.gg/umAuPM9KCJ"
        target="_blank"
        ><img
          class="small-logo"
          id="discord-logo"
          alt="discord logo"
          src={currentDiscordImageSrc}
          on:mouseover={discord_hover}
          on:mouseout={discord_unhover} />
      </a>
    </div>
  </div>

  <img class="fade-in" id="scroll-down" alt="scroll down" src={scrollDown} />
</div>

<style>
  @import "../../styles/fonts.css";

  a {
    text-decoration: none;
  }

  #about-container {
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
    align-items: center;
  }

  #logo {
    width: 70%;
    height: auto;
    pointer-events: none;
    opacity: 0;
    transition: opacity 0.25s;
    margin-bottom: 2em;
  }

  @media (max-width: 800px) {
    #logo {
      width: 90%;
    }
  }

  .subheader-text {
    display: flex;
    margin-top: 2vh;
    font-family: "Monogram", monospace;
    font-size: 4rem;
    font-weight: normal;
    transition: font-family 0.5s ease-in-out;
    color: #fffee9;
    margin-bottom: 0.25em;
    pointer-events: none;
  }

  .subheader-container {
    display: flex;
    justify-content: center;
    width: 100%;
    height: min-content;
    margin-top: 2.7vh;
    align-items: center;
    flex-direction: column;
    line-height: 0;
  }

  #s-logo-container {
    position: relative;
    display: block;
    margin: auto;
  }

  .small-logo {
    width: auto;
    height: clamp(2rem, 5vw, 10rem);
    transform: translate(0, 12px);
    margin-top: 1.5vw;
  }

  .fade-in {
    opacity: 0;
    transition: opacity 3s;
  }

  #scroll-down {
    width: auto;
    height: clamp(1.5rem, 3vw, 10rem);
    position: absolute;
    left: 50%;
    bottom: 10px;
    transform: translate(-50%, -50%);
    margin: 0 auto;
    opacity: 0;
    transition: opacity 2s ease-in-out;
    animation: float 2s cubic-bezier(0.42, 0, 0.5, 1) infinite;
  }

  @keyframes float {
    0% {
      transform: translate(-50%, -50%);
    }
    50% {
      transform: translate(-50%, -30%);
    }
  }
</style>
