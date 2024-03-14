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
  let scrollDown = "/assets/scroll.svg";
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
        ><svg
          version="1.1"
          width=""
          height=""
          xmlns="http://www.w3.org/2000/svg"
          shape-rendering="crispEdges"
          viewBox="0 0 20 20">
          <rect x="8" y="1" width="1" height="1" fill="none" />
          <rect x="9" y="1" width="1" height="1" fill="none" />
          <rect x="10" y="1" width="1" height="1" fill="none" />
          <rect x="11" y="1" width="1" height="1" fill="none" />
          <rect x="6" y="2" width="1" height="1" fill="none" />
          <rect x="7" y="2" width="1" height="1" fill="none" />
          <rect x="8" y="2" width="1" height="1" fill="none" />
          <rect x="9" y="2" width="1" height="1" fill="none" />
          <rect x="10" y="2" width="1" height="1" fill="none" />
          <rect x="11" y="2" width="1" height="1" fill="none" />
          <rect x="12" y="2" width="1" height="1" fill="none" />
          <rect x="13" y="2" width="1" height="1" fill="none" />
          <rect x="5" y="3" width="1" height="1" fill="none" />
          <rect x="6" y="3" width="1" height="1" fill="none" />
          <rect x="7" y="3" width="1" height="1" fill="none" />
          <rect x="8" y="3" width="1" height="1" fill="none" />
          <rect x="9" y="3" width="1" height="1" fill="none" />
          <rect x="10" y="3" width="1" height="1" fill="none" />
          <rect x="11" y="3" width="1" height="1" fill="none" />
          <rect x="12" y="3" width="1" height="1" fill="none" />
          <rect x="13" y="3" width="1" height="1" fill="none" />
          <rect x="14" y="3" width="1" height="1" fill="none" />
          <rect x="4" y="4" width="1" height="1" fill="none" />
          <rect x="5" y="4" width="1" height="1" fill="none" />
          <rect x="6" y="4" width="1" height="1" fill="none" />
          <rect x="7" y="4" width="1" height="1" fill="none" />
          <rect x="8" y="4" width="1" height="1" fill="none" />
          <rect x="9" y="4" width="1" height="1" fill="none" />
          <rect x="10" y="4" width="1" height="1" fill="none" />
          <rect x="11" y="4" width="1" height="1" fill="none" />
          <rect x="12" y="4" width="1" height="1" fill="none" />
          <rect x="13" y="4" width="1" height="1" fill="none" />
          <rect x="14" y="4" width="1" height="1" fill="none" />
          <rect x="15" y="4" width="1" height="1" fill="none" />
          <rect x="3" y="5" width="1" height="1" fill="none" />
          <rect x="4" y="5" width="1" height="1" fill="none" />
          <rect x="5" y="5" width="1" height="1" fill="none" />
          <rect x="6" y="5" width="1" height="1" fill="none" />
          <rect x="7" y="5" width="1" height="1" fill="none" />
          <rect x="8" y="5" width="1" height="1" fill="none" />
          <rect x="9" y="5" width="1" height="1" fill="none" />
          <rect x="10" y="5" width="1" height="1" fill="none" />
          <rect x="11" y="5" width="1" height="1" fill="currentColor" />
          <rect x="12" y="5" width="1" height="1" fill="currentColor" />
          <rect x="13" y="5" width="1" height="1" fill="currentColor" />
          <rect x="14" y="5" width="1" height="1" fill="none" />
          <rect x="15" y="5" width="1" height="1" fill="none" />
          <rect x="16" y="5" width="1" height="1" fill="none" />
          <rect x="2" y="6" width="1" height="1" fill="none" />
          <rect x="3" y="6" width="1" height="1" fill="none" />
          <rect x="4" y="6" width="1" height="1" fill="none" />
          <rect x="5" y="6" width="1" height="1" fill="none" />
          <rect x="6" y="6" width="1" height="1" fill="none" />
          <rect x="7" y="6" width="1" height="1" fill="none" />
          <rect x="8" y="6" width="1" height="1" fill="none" />
          <rect x="9" y="6" width="1" height="1" fill="none" />
          <rect x="10" y="6" width="1" height="1" fill="currentColor" />
          <rect x="11" y="6" width="1" height="1" fill="none" />
          <rect x="12" y="6" width="1" height="1" fill="none" />
          <rect x="13" y="6" width="1" height="1" fill="none" />
          <rect x="14" y="6" width="1" height="1" fill="currentColor" />
          <rect x="15" y="6" width="1" height="1" fill="none" />
          <rect x="16" y="6" width="1" height="1" fill="none" />
          <rect x="17" y="6" width="1" height="1" fill="none" />
          <rect x="2" y="7" width="1" height="1" fill="none" />
          <rect x="3" y="7" width="1" height="1" fill="none" />
          <rect x="4" y="7" width="1" height="1" fill="none" />
          <rect x="5" y="7" width="1" height="1" fill="none" />
          <rect x="6" y="7" width="1" height="1" fill="none" />
          <rect x="7" y="7" width="1" height="1" fill="none" />
          <rect x="8" y="7" width="1" height="1" fill="none" />
          <rect x="9" y="7" width="1" height="1" fill="currentColor" />
          <rect x="10" y="7" width="1" height="1" fill="none" />
          <rect x="11" y="7" width="1" height="1" fill="currentColor" />
          <rect x="12" y="7" width="1" height="1" fill="currentColor" />
          <rect x="13" y="7" width="1" height="1" fill="currentColor" />
          <rect x="14" y="7" width="1" height="1" fill="none" />
          <rect x="15" y="7" width="1" height="1" fill="currentColor" />
          <rect x="16" y="7" width="1" height="1" fill="none" />
          <rect x="17" y="7" width="1" height="1" fill="none" />
          <rect x="1" y="8" width="1" height="1" fill="none" />
          <rect x="2" y="8" width="1" height="1" fill="currentColor" />
          <rect x="3" y="8" width="1" height="1" fill="none" />
          <rect x="4" y="8" width="1" height="1" fill="none" />
          <rect x="5" y="8" width="1" height="1" fill="none" />
          <rect x="6" y="8" width="1" height="1" fill="none" />
          <rect x="7" y="8" width="1" height="1" fill="none" />
          <rect x="8" y="8" width="1" height="1" fill="none" />
          <rect x="9" y="8" width="1" height="1" fill="currentColor" />
          <rect x="10" y="8" width="1" height="1" fill="none" />
          <rect x="11" y="8" width="1" height="1" fill="currentColor" />
          <rect x="12" y="8" width="1" height="1" fill="currentColor" />
          <rect x="13" y="8" width="1" height="1" fill="currentColor" />
          <rect x="14" y="8" width="1" height="1" fill="none" />
          <rect x="15" y="8" width="1" height="1" fill="currentColor" />
          <rect x="16" y="8" width="1" height="1" fill="none" />
          <rect x="17" y="8" width="1" height="1" fill="none" />
          <rect x="18" y="8" width="1" height="1" fill="none" />
          <rect x="1" y="9" width="1" height="1" fill="none" />
          <rect x="2" y="9" width="1" height="1" fill="currentColor" />
          <rect x="3" y="9" width="1" height="1" fill="currentColor" />
          <rect x="4" y="9" width="1" height="1" fill="currentColor" />
          <rect x="5" y="9" width="1" height="1" fill="none" />
          <rect x="6" y="9" width="1" height="1" fill="none" />
          <rect x="7" y="9" width="1" height="1" fill="none" />
          <rect x="8" y="9" width="1" height="1" fill="none" />
          <rect x="9" y="9" width="1" height="1" fill="currentColor" />
          <rect x="10" y="9" width="1" height="1" fill="none" />
          <rect x="11" y="9" width="1" height="1" fill="currentColor" />
          <rect x="12" y="9" width="1" height="1" fill="currentColor" />
          <rect x="13" y="9" width="1" height="1" fill="currentColor" />
          <rect x="14" y="9" width="1" height="1" fill="none" />
          <rect x="15" y="9" width="1" height="1" fill="currentColor" />
          <rect x="16" y="9" width="1" height="1" fill="none" />
          <rect x="17" y="9" width="1" height="1" fill="none" />
          <rect x="18" y="9" width="1" height="1" fill="none" />
          <rect x="1" y="10" width="1" height="1" fill="none" />
          <rect x="2" y="10" width="1" height="1" fill="currentColor" />
          <rect x="3" y="10" width="1" height="1" fill="currentColor" />
          <rect x="4" y="10" width="1" height="1" fill="currentColor" />
          <rect x="5" y="10" width="1" height="1" fill="currentColor" />
          <rect x="6" y="10" width="1" height="1" fill="none" />
          <rect x="7" y="10" width="1" height="1" fill="currentColor" />
          <rect x="8" y="10" width="1" height="1" fill="currentColor" />
          <rect x="9" y="10" width="1" height="1" fill="currentColor" />
          <rect x="10" y="10" width="1" height="1" fill="currentColor" />
          <rect x="11" y="10" width="1" height="1" fill="none" />
          <rect x="12" y="10" width="1" height="1" fill="none" />
          <rect x="13" y="10" width="1" height="1" fill="none" />
          <rect x="14" y="10" width="1" height="1" fill="currentColor" />
          <rect x="15" y="10" width="1" height="1" fill="none" />
          <rect x="16" y="10" width="1" height="1" fill="none" />
          <rect x="17" y="10" width="1" height="1" fill="none" />
          <rect x="18" y="10" width="1" height="1" fill="none" />
          <rect x="1" y="11" width="1" height="1" fill="none" />
          <rect x="2" y="11" width="1" height="1" fill="none" />
          <rect x="3" y="11" width="1" height="1" fill="currentColor" />
          <rect x="4" y="11" width="1" height="1" fill="currentColor" />
          <rect x="5" y="11" width="1" height="1" fill="currentColor" />
          <rect x="6" y="11" width="1" height="1" fill="currentColor" />
          <rect x="7" y="11" width="1" height="1" fill="currentColor" />
          <rect x="8" y="11" width="1" height="1" fill="none" />
          <rect x="9" y="11" width="1" height="1" fill="currentColor" />
          <rect x="10" y="11" width="1" height="1" fill="currentColor" />
          <rect x="11" y="11" width="1" height="1" fill="currentColor" />
          <rect x="12" y="11" width="1" height="1" fill="currentColor" />
          <rect x="13" y="11" width="1" height="1" fill="currentColor" />
          <rect x="14" y="11" width="1" height="1" fill="none" />
          <rect x="15" y="11" width="1" height="1" fill="none" />
          <rect x="16" y="11" width="1" height="1" fill="none" />
          <rect x="17" y="11" width="1" height="1" fill="none" />
          <rect x="18" y="11" width="1" height="1" fill="none" />
          <rect x="2" y="12" width="1" height="1" fill="none" />
          <rect x="3" y="12" width="1" height="1" fill="none" />
          <rect x="4" y="12" width="1" height="1" fill="currentColor" />
          <rect x="5" y="12" width="1" height="1" fill="currentColor" />
          <rect x="6" y="12" width="1" height="1" fill="currentColor" />
          <rect x="7" y="12" width="1" height="1" fill="currentColor" />
          <rect x="8" y="12" width="1" height="1" fill="currentColor" />
          <rect x="9" y="12" width="1" height="1" fill="none" />
          <rect x="10" y="12" width="1" height="1" fill="currentColor" />
          <rect x="11" y="12" width="1" height="1" fill="none" />
          <rect x="12" y="12" width="1" height="1" fill="none" />
          <rect x="13" y="12" width="1" height="1" fill="none" />
          <rect x="14" y="12" width="1" height="1" fill="none" />
          <rect x="15" y="12" width="1" height="1" fill="none" />
          <rect x="16" y="12" width="1" height="1" fill="none" />
          <rect x="17" y="12" width="1" height="1" fill="none" />
          <rect x="2" y="13" width="1" height="1" fill="none" />
          <rect x="3" y="13" width="1" height="1" fill="none" />
          <rect x="4" y="13" width="1" height="1" fill="none" />
          <rect x="5" y="13" width="1" height="1" fill="currentColor" />
          <rect x="6" y="13" width="1" height="1" fill="none" />
          <rect x="7" y="13" width="1" height="1" fill="currentColor" />
          <rect x="8" y="13" width="1" height="1" fill="currentColor" />
          <rect x="9" y="13" width="1" height="1" fill="none" />
          <rect x="10" y="13" width="1" height="1" fill="currentColor" />
          <rect x="11" y="13" width="1" height="1" fill="none" />
          <rect x="12" y="13" width="1" height="1" fill="none" />
          <rect x="13" y="13" width="1" height="1" fill="none" />
          <rect x="14" y="13" width="1" height="1" fill="none" />
          <rect x="15" y="13" width="1" height="1" fill="none" />
          <rect x="16" y="13" width="1" height="1" fill="none" />
          <rect x="17" y="13" width="1" height="1" fill="none" />
          <rect x="3" y="14" width="1" height="1" fill="none" />
          <rect x="4" y="14" width="1" height="1" fill="none" />
          <rect x="5" y="14" width="1" height="1" fill="none" />
          <rect x="6" y="14" width="1" height="1" fill="currentColor" />
          <rect x="7" y="14" width="1" height="1" fill="none" />
          <rect x="8" y="14" width="1" height="1" fill="none" />
          <rect x="9" y="14" width="1" height="1" fill="currentColor" />
          <rect x="10" y="14" width="1" height="1" fill="none" />
          <rect x="11" y="14" width="1" height="1" fill="none" />
          <rect x="12" y="14" width="1" height="1" fill="none" />
          <rect x="13" y="14" width="1" height="1" fill="none" />
          <rect x="14" y="14" width="1" height="1" fill="none" />
          <rect x="15" y="14" width="1" height="1" fill="none" />
          <rect x="16" y="14" width="1" height="1" fill="none" />
          <rect x="4" y="15" width="1" height="1" fill="none" />
          <rect x="5" y="15" width="1" height="1" fill="none" />
          <rect x="6" y="15" width="1" height="1" fill="none" />
          <rect x="7" y="15" width="1" height="1" fill="currentColor" />
          <rect x="8" y="15" width="1" height="1" fill="currentColor" />
          <rect x="9" y="15" width="1" height="1" fill="none" />
          <rect x="10" y="15" width="1" height="1" fill="none" />
          <rect x="11" y="15" width="1" height="1" fill="none" />
          <rect x="12" y="15" width="1" height="1" fill="none" />
          <rect x="13" y="15" width="1" height="1" fill="none" />
          <rect x="14" y="15" width="1" height="1" fill="none" />
          <rect x="15" y="15" width="1" height="1" fill="none" />
          <rect x="5" y="16" width="1" height="1" fill="none" />
          <rect x="6" y="16" width="1" height="1" fill="none" />
          <rect x="7" y="16" width="1" height="1" fill="none" />
          <rect x="8" y="16" width="1" height="1" fill="none" />
          <rect x="9" y="16" width="1" height="1" fill="none" />
          <rect x="10" y="16" width="1" height="1" fill="none" />
          <rect x="11" y="16" width="1" height="1" fill="none" />
          <rect x="12" y="16" width="1" height="1" fill="none" />
          <rect x="13" y="16" width="1" height="1" fill="none" />
          <rect x="14" y="16" width="1" height="1" fill="none" />
          <rect x="6" y="17" width="1" height="1" fill="none" />
          <rect x="7" y="17" width="1" height="1" fill="none" />
          <rect x="8" y="17" width="1" height="1" fill="none" />
          <rect x="9" y="17" width="1" height="1" fill="none" />
          <rect x="10" y="17" width="1" height="1" fill="none" />
          <rect x="11" y="17" width="1" height="1" fill="none" />
          <rect x="12" y="17" width="1" height="1" fill="none" />
          <rect x="13" y="17" width="1" height="1" fill="none" />
          <rect x="8" y="18" width="1" height="1" fill="none" />
          <rect x="9" y="18" width="1" height="1" fill="none" />
          <rect x="10" y="18" width="1" height="1" fill="none" />
          <rect x="11" y="18" width="1" height="1" fill="none" />
        </svg></a>
      <a
        title="Free Will Community Discord"
        href="https://discord.gg/umAuPM9KCJ"
        target="_blank"
        ><svg
          version="1.1"
          width=""
          height=""
          xmlns="http://www.w3.org/2000/svg"
          shape-rendering="crispEdges"
          viewBox="0 0 20 20">
          <rect x="8" y="1" width="1" height="1" fill="none" />
          <rect x="9" y="1" width="1" height="1" fill="none" />
          <rect x="10" y="1" width="1" height="1" fill="none" />
          <rect x="11" y="1" width="1" height="1" fill="none" />
          <rect x="6" y="2" width="1" height="1" fill="none" />
          <rect x="7" y="2" width="1" height="1" fill="none" />
          <rect x="8" y="2" width="1" height="1" fill="none" />
          <rect x="9" y="2" width="1" height="1" fill="none" />
          <rect x="10" y="2" width="1" height="1" fill="none" />
          <rect x="11" y="2" width="1" height="1" fill="none" />
          <rect x="12" y="2" width="1" height="1" fill="none" />
          <rect x="13" y="2" width="1" height="1" fill="none" />
          <rect x="5" y="3" width="1" height="1" fill="none" />
          <rect x="6" y="3" width="1" height="1" fill="none" />
          <rect x="7" y="3" width="1" height="1" fill="none" />
          <rect x="8" y="3" width="1" height="1" fill="none" />
          <rect x="9" y="3" width="1" height="1" fill="none" />
          <rect x="10" y="3" width="1" height="1" fill="none" />
          <rect x="11" y="3" width="1" height="1" fill="none" />
          <rect x="12" y="3" width="1" height="1" fill="none" />
          <rect x="13" y="3" width="1" height="1" fill="none" />
          <rect x="14" y="3" width="1" height="1" fill="none" />
          <rect x="4" y="4" width="1" height="1" fill="none" />
          <rect x="5" y="4" width="1" height="1" fill="none" />
          <rect x="6" y="4" width="1" height="1" fill="none" />
          <rect x="7" y="4" width="1" height="1" fill="none" />
          <rect x="8" y="4" width="1" height="1" fill="none" />
          <rect x="9" y="4" width="1" height="1" fill="none" />
          <rect x="10" y="4" width="1" height="1" fill="none" />
          <rect x="11" y="4" width="1" height="1" fill="none" />
          <rect x="12" y="4" width="1" height="1" fill="none" />
          <rect x="13" y="4" width="1" height="1" fill="none" />
          <rect x="14" y="4" width="1" height="1" fill="none" />
          <rect x="15" y="4" width="1" height="1" fill="none" />
          <rect x="3" y="5" width="1" height="1" fill="none" />
          <rect x="4" y="5" width="1" height="1" fill="none" />
          <rect x="5" y="5" width="1" height="1" fill="none" />
          <rect x="6" y="5" width="1" height="1" fill="currentColor" />
          <rect x="7" y="5" width="1" height="1" fill="currentColor" />
          <rect x="8" y="5" width="1" height="1" fill="none" />
          <rect x="9" y="5" width="1" height="1" fill="none" />
          <rect x="10" y="5" width="1" height="1" fill="none" />
          <rect x="11" y="5" width="1" height="1" fill="none" />
          <rect x="12" y="5" width="1" height="1" fill="currentColor" />
          <rect x="13" y="5" width="1" height="1" fill="currentColor" />
          <rect x="14" y="5" width="1" height="1" fill="none" />
          <rect x="15" y="5" width="1" height="1" fill="none" />
          <rect x="16" y="5" width="1" height="1" fill="none" />
          <rect x="2" y="6" width="1" height="1" fill="none" />
          <rect x="3" y="6" width="1" height="1" fill="none" />
          <rect x="4" y="6" width="1" height="1" fill="none" />
          <rect x="5" y="6" width="1" height="1" fill="currentColor" />
          <rect x="6" y="6" width="1" height="1" fill="currentColor" />
          <rect x="7" y="6" width="1" height="1" fill="currentColor" />
          <rect x="8" y="6" width="1" height="1" fill="currentColor" />
          <rect x="9" y="6" width="1" height="1" fill="currentColor" />
          <rect x="10" y="6" width="1" height="1" fill="currentColor" />
          <rect x="11" y="6" width="1" height="1" fill="currentColor" />
          <rect x="12" y="6" width="1" height="1" fill="currentColor" />
          <rect x="13" y="6" width="1" height="1" fill="currentColor" />
          <rect x="14" y="6" width="1" height="1" fill="currentColor" />
          <rect x="15" y="6" width="1" height="1" fill="none" />
          <rect x="16" y="6" width="1" height="1" fill="none" />
          <rect x="17" y="6" width="1" height="1" fill="none" />
          <rect x="2" y="7" width="1" height="1" fill="none" />
          <rect x="3" y="7" width="1" height="1" fill="none" />
          <rect x="4" y="7" width="1" height="1" fill="none" />
          <rect x="5" y="7" width="1" height="1" fill="currentColor" />
          <rect x="6" y="7" width="1" height="1" fill="currentColor" />
          <rect x="7" y="7" width="1" height="1" fill="currentColor" />
          <rect x="8" y="7" width="1" height="1" fill="currentColor" />
          <rect x="9" y="7" width="1" height="1" fill="currentColor" />
          <rect x="10" y="7" width="1" height="1" fill="currentColor" />
          <rect x="11" y="7" width="1" height="1" fill="currentColor" />
          <rect x="12" y="7" width="1" height="1" fill="currentColor" />
          <rect x="13" y="7" width="1" height="1" fill="currentColor" />
          <rect x="14" y="7" width="1" height="1" fill="currentColor" />
          <rect x="15" y="7" width="1" height="1" fill="none" />
          <rect x="16" y="7" width="1" height="1" fill="none" />
          <rect x="17" y="7" width="1" height="1" fill="none" />
          <rect x="1" y="8" width="1" height="1" fill="none" />
          <rect x="2" y="8" width="1" height="1" fill="none" />
          <rect x="3" y="8" width="1" height="1" fill="none" />
          <rect x="4" y="8" width="1" height="1" fill="none" />
          <rect x="5" y="8" width="1" height="1" fill="currentColor" />
          <rect x="6" y="8" width="1" height="1" fill="currentColor" />
          <rect x="7" y="8" width="1" height="1" fill="currentColor" />
          <rect x="8" y="8" width="1" height="1" fill="currentColor" />
          <rect x="9" y="8" width="1" height="1" fill="currentColor" />
          <rect x="10" y="8" width="1" height="1" fill="currentColor" />
          <rect x="11" y="8" width="1" height="1" fill="currentColor" />
          <rect x="12" y="8" width="1" height="1" fill="currentColor" />
          <rect x="13" y="8" width="1" height="1" fill="currentColor" />
          <rect x="14" y="8" width="1" height="1" fill="currentColor" />
          <rect x="15" y="8" width="1" height="1" fill="none" />
          <rect x="16" y="8" width="1" height="1" fill="none" />
          <rect x="17" y="8" width="1" height="1" fill="none" />
          <rect x="18" y="8" width="1" height="1" fill="none" />
          <rect x="1" y="9" width="1" height="1" fill="none" />
          <rect x="2" y="9" width="1" height="1" fill="none" />
          <rect x="3" y="9" width="1" height="1" fill="none" />
          <rect x="4" y="9" width="1" height="1" fill="currentColor" />
          <rect x="5" y="9" width="1" height="1" fill="currentColor" />
          <rect x="6" y="9" width="1" height="1" fill="currentColor" />
          <rect x="7" y="9" width="1" height="1" fill="none" />
          <rect x="8" y="9" width="1" height="1" fill="none" />
          <rect x="9" y="9" width="1" height="1" fill="currentColor" />
          <rect x="10" y="9" width="1" height="1" fill="currentColor" />
          <rect x="11" y="9" width="1" height="1" fill="none" />
          <rect x="12" y="9" width="1" height="1" fill="none" />
          <rect x="13" y="9" width="1" height="1" fill="currentColor" />
          <rect x="14" y="9" width="1" height="1" fill="currentColor" />
          <rect x="15" y="9" width="1" height="1" fill="currentColor" />
          <rect x="16" y="9" width="1" height="1" fill="none" />
          <rect x="17" y="9" width="1" height="1" fill="none" />
          <rect x="18" y="9" width="1" height="1" fill="none" />
          <rect x="1" y="10" width="1" height="1" fill="none" />
          <rect x="2" y="10" width="1" height="1" fill="none" />
          <rect x="3" y="10" width="1" height="1" fill="none" />
          <rect x="4" y="10" width="1" height="1" fill="currentColor" />
          <rect x="5" y="10" width="1" height="1" fill="currentColor" />
          <rect x="6" y="10" width="1" height="1" fill="currentColor" />
          <rect x="7" y="10" width="1" height="1" fill="none" />
          <rect x="8" y="10" width="1" height="1" fill="none" />
          <rect x="9" y="10" width="1" height="1" fill="currentColor" />
          <rect x="10" y="10" width="1" height="1" fill="currentColor" />
          <rect x="11" y="10" width="1" height="1" fill="none" />
          <rect x="12" y="10" width="1" height="1" fill="none" />
          <rect x="13" y="10" width="1" height="1" fill="currentColor" />
          <rect x="14" y="10" width="1" height="1" fill="currentColor" />
          <rect x="15" y="10" width="1" height="1" fill="currentColor" />
          <rect x="16" y="10" width="1" height="1" fill="none" />
          <rect x="17" y="10" width="1" height="1" fill="none" />
          <rect x="18" y="10" width="1" height="1" fill="none" />
          <rect x="1" y="11" width="1" height="1" fill="none" />
          <rect x="2" y="11" width="1" height="1" fill="none" />
          <rect x="3" y="11" width="1" height="1" fill="none" />
          <rect x="4" y="11" width="1" height="1" fill="currentColor" />
          <rect x="5" y="11" width="1" height="1" fill="currentColor" />
          <rect x="6" y="11" width="1" height="1" fill="currentColor" />
          <rect x="7" y="11" width="1" height="1" fill="currentColor" />
          <rect x="8" y="11" width="1" height="1" fill="currentColor" />
          <rect x="9" y="11" width="1" height="1" fill="currentColor" />
          <rect x="10" y="11" width="1" height="1" fill="currentColor" />
          <rect x="11" y="11" width="1" height="1" fill="currentColor" />
          <rect x="12" y="11" width="1" height="1" fill="currentColor" />
          <rect x="13" y="11" width="1" height="1" fill="currentColor" />
          <rect x="14" y="11" width="1" height="1" fill="currentColor" />
          <rect x="15" y="11" width="1" height="1" fill="currentColor" />
          <rect x="16" y="11" width="1" height="1" fill="none" />
          <rect x="17" y="11" width="1" height="1" fill="none" />
          <rect x="18" y="11" width="1" height="1" fill="none" />
          <rect x="2" y="12" width="1" height="1" fill="none" />
          <rect x="3" y="12" width="1" height="1" fill="none" />
          <rect x="4" y="12" width="1" height="1" fill="currentColor" />
          <rect x="5" y="12" width="1" height="1" fill="currentColor" />
          <rect x="6" y="12" width="1" height="1" fill="none" />
          <rect x="7" y="12" width="1" height="1" fill="currentColor" />
          <rect x="8" y="12" width="1" height="1" fill="currentColor" />
          <rect x="9" y="12" width="1" height="1" fill="currentColor" />
          <rect x="10" y="12" width="1" height="1" fill="currentColor" />
          <rect x="11" y="12" width="1" height="1" fill="currentColor" />
          <rect x="12" y="12" width="1" height="1" fill="currentColor" />
          <rect x="13" y="12" width="1" height="1" fill="none" />
          <rect x="14" y="12" width="1" height="1" fill="currentColor" />
          <rect x="15" y="12" width="1" height="1" fill="currentColor" />
          <rect x="16" y="12" width="1" height="1" fill="none" />
          <rect x="17" y="12" width="1" height="1" fill="none" />
          <rect x="2" y="13" width="1" height="1" fill="none" />
          <rect x="3" y="13" width="1" height="1" fill="none" />
          <rect x="4" y="13" width="1" height="1" fill="none" />
          <rect x="5" y="13" width="1" height="1" fill="currentColor" />
          <rect x="6" y="13" width="1" height="1" fill="currentColor" />
          <rect x="7" y="13" width="1" height="1" fill="none" />
          <rect x="8" y="13" width="1" height="1" fill="none" />
          <rect x="9" y="13" width="1" height="1" fill="none" />
          <rect x="10" y="13" width="1" height="1" fill="none" />
          <rect x="11" y="13" width="1" height="1" fill="none" />
          <rect x="12" y="13" width="1" height="1" fill="none" />
          <rect x="13" y="13" width="1" height="1" fill="currentColor" />
          <rect x="14" y="13" width="1" height="1" fill="currentColor" />
          <rect x="15" y="13" width="1" height="1" fill="none" />
          <rect x="16" y="13" width="1" height="1" fill="none" />
          <rect x="17" y="13" width="1" height="1" fill="none" />
          <rect x="3" y="14" width="1" height="1" fill="none" />
          <rect x="4" y="14" width="1" height="1" fill="none" />
          <rect x="5" y="14" width="1" height="1" fill="none" />
          <rect x="6" y="14" width="1" height="1" fill="none" />
          <rect x="7" y="14" width="1" height="1" fill="none" />
          <rect x="8" y="14" width="1" height="1" fill="none" />
          <rect x="9" y="14" width="1" height="1" fill="none" />
          <rect x="10" y="14" width="1" height="1" fill="none" />
          <rect x="11" y="14" width="1" height="1" fill="none" />
          <rect x="12" y="14" width="1" height="1" fill="none" />
          <rect x="13" y="14" width="1" height="1" fill="none" />
          <rect x="14" y="14" width="1" height="1" fill="none" />
          <rect x="15" y="14" width="1" height="1" fill="none" />
          <rect x="16" y="14" width="1" height="1" fill="none" />
          <rect x="4" y="15" width="1" height="1" fill="none" />
          <rect x="5" y="15" width="1" height="1" fill="none" />
          <rect x="6" y="15" width="1" height="1" fill="none" />
          <rect x="7" y="15" width="1" height="1" fill="none" />
          <rect x="8" y="15" width="1" height="1" fill="none" />
          <rect x="9" y="15" width="1" height="1" fill="none" />
          <rect x="10" y="15" width="1" height="1" fill="none" />
          <rect x="11" y="15" width="1" height="1" fill="none" />
          <rect x="12" y="15" width="1" height="1" fill="none" />
          <rect x="13" y="15" width="1" height="1" fill="none" />
          <rect x="14" y="15" width="1" height="1" fill="none" />
          <rect x="15" y="15" width="1" height="1" fill="none" />
          <rect x="5" y="16" width="1" height="1" fill="none" />
          <rect x="6" y="16" width="1" height="1" fill="none" />
          <rect x="7" y="16" width="1" height="1" fill="none" />
          <rect x="8" y="16" width="1" height="1" fill="none" />
          <rect x="9" y="16" width="1" height="1" fill="none" />
          <rect x="10" y="16" width="1" height="1" fill="none" />
          <rect x="11" y="16" width="1" height="1" fill="none" />
          <rect x="12" y="16" width="1" height="1" fill="none" />
          <rect x="13" y="16" width="1" height="1" fill="none" />
          <rect x="14" y="16" width="1" height="1" fill="none" />
          <rect x="6" y="17" width="1" height="1" fill="none" />
          <rect x="7" y="17" width="1" height="1" fill="none" />
          <rect x="8" y="17" width="1" height="1" fill="none" />
          <rect x="9" y="17" width="1" height="1" fill="none" />
          <rect x="10" y="17" width="1" height="1" fill="none" />
          <rect x="11" y="17" width="1" height="1" fill="none" />
          <rect x="12" y="17" width="1" height="1" fill="none" />
          <rect x="13" y="17" width="1" height="1" fill="none" />
          <rect x="8" y="18" width="1" height="1" fill="none" />
          <rect x="9" y="18" width="1" height="1" fill="none" />
          <rect x="10" y="18" width="1" height="1" fill="none" />
          <rect x="11" y="18" width="1" height="1" fill="none" />
        </svg>
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

  #s-logo-container svg {
    width: 60px;
    height: 60px;
    color: rgb(255, 254, 233);
    transition: color 0.2s ease-in-out;
    transform: translate(0, 12px);
    margin-top: 1.5vw;
  }

  #s-logo-container svg:hover {
    color: red;
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
