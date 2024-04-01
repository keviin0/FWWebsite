<script>
  import { onMount } from "svelte";
  import SmallSpacer from "$lib/components/SmallSpacer.svelte";

  let willSprite = "/assets/will_sprite.svg";
  let windows = "/assets/windows_logo_white.svg";
  let trailer_video = "/assets/fwtrailer.mp4";

  let imageNamePattern = "p";
  let imageExtension = ".png";
  let totalImages = 10;
  let images = [];

  for (let i = 1; i <= totalImages; i++) {
    images.push(`${imageNamePattern}${i}${imageExtension}`);
  }

  const clamp = (num, min, max) => Math.min(Math.max(num, min), max);

  onMount(() => {
    var circularText = document.querySelector(".context-text p");
    circularText.innerHTML = circularText.innerText
      .split("")
      .map(
        (char, i) =>
          `<span style="transform:rotate(${i * 22.5}deg) translate(0, -100%); color: #FFFEE9; position: absolute; font-size: 2.5em; transform-origin: 0px 86px; left: 50%; font-family: DotGothic16, sans-serif;">${char}</span>`
      )
      .join("");

    circularText = document.querySelector(".os-text p");
    circularText.innerHTML = circularText.innerText
      .split("")
      .map(
        (char, i) =>
          `<span style="transform:rotate(${i * 20}deg) translate(0, -100%); color: #FFFEE9; position: absolute; font-size: 2.5em; transform-origin: 0px 86px; left: 50%; font-family: DotGothic16, sans-serif;">${char}</span>`
      )
      .join("");

    addEventListener("scroll", (event) => {
      updateScrollRotation();
    });
  });

  async function updateScrollRotation() {
    var elements = document.querySelectorAll(".hovering-picture");
    var topContainer = document.querySelector("#context-container");
    var bottomContainer = document.querySelector("#os-inner-container");

    if (!elements || !topContainer || !bottomContainer) return;

    var bottomVal = bottomContainer.getBoundingClientRect().bottom;
    var topVal = topContainer.getBoundingClientRect().top;
    var scrollPercentage = clamp(
      (window.innerHeight - topVal) / (bottomVal - topVal),
      0.6,
      1.8
    );

    elements.forEach(function (element) {
      var translateYValue = 65 - scrollPercentage * 65;
      var rotateValue = 20 - scrollPercentage * 20;

      element.style.setProperty("--translateY", `${translateYValue}px`);
      element.style.setProperty("--rotate", `${rotateValue}deg`);
    });
  }
</script>

<div class="wrapper">
  <div class="container">
    <div class="section-label trailer">TRAILER</div>
    <div id="trailer-container" class="section-item">
      <div id="trailer-video-container">
        <!-- svelte-ignore a11y-media-has-caption -->
        <video id="trailer-video" controls>
          <source src={trailer_video} type="video/mp4" />
        </video>
      </div>
    </div>
    <SmallSpacer />

    <div class="section-label">ABOUT OUR GAME</div>
    <div class="section-subtext">
      Free Will is a <strong
        >2D psychological puzzle RPG suffering from corruption</strong
      >. Playing this game means you accept the responsibility of cleansing
      Corruption from its system.
    </div>
    <SmallSpacer />

    <div id="context-container" class="section-row reversed-section-item">
      <div
        id="context-inner-container"
        class="image-section left-section-inner title">
        <div class="circle">
          <img
            id="will-sprite"
            alt="will sprite"
            class="hovering-picture"
            src={willSprite} />
        </div>
      </div>
      <div
        id="context-description-container"
        class="description-section right-section-inner">
        <div id="context-description-text" class="regular-text">
          <h1>STORY</h1>
          <p>
            Control Will, a young boy who has been bedridden for most of his
            life, as he fights against reality-breaking monsters.<br /><br />
            Watch as Will tries to understand the depth of his own autonomy.
            <br /><br />
            And play out <strong>your role</strong> in cleansing the game.
          </p>
        </div>
      </div>
    </div>
    <SmallSpacer />

    <div id="feature-container" class="section-row section-item">
      <div
        id="os-inner-container"
        class="image-section left-section-inner title">
        <div class="circle">
          <img alt="windows logo" class="hovering-picture" src={windows} />
        </div>
      </div>
      <div
        id="os-video-container"
        class="right-section-inner description-section">
        <!-- svelte-ignore a11y-media-has-caption -->
        <div id="os-description-text" class="regular-text">
          <h1>FEATURES</h1>
          <ul>
            <li>
              Manipulate the game's file structure through metapuzzles to
              influence Will's world.
            </li>
            <li>Get to know Will--he knows you are there…</li>
            <li>Cleanse the corruption. For there is no other way forward.</li>
            <li>
              Unearth ̸i̶n̵f̷o̴r̶m̸a̷t̵i̴o̵n̸ ̸t̶h̶a̸t̷ ̶̃̕the inhabitants ̵͂̽ô̶͝f̶́ this ̄̈́h̵̐ou̅s̸e might b͑͛ȅ̴͊
              ̶̂̾b̸̀̑ĕ̷͕t̷̽ter off not k̴̈́nowing.
            </li>
          </ul>
        </div>
      </div>
    </div>
    <div class="screenshot-label regular-text">
      <h1>SCREENSHOTS</h1>
    </div>
    <div class="screenshots section-row">
      {#each images as image}
        <a target="_blank" href={`/assets/screenshots/${image}`}>
          <img class="image" src={`/assets/screenshots/${image}`} alt={image} />
        </a>
      {/each}
    </div>
  </div>
</div>

<style>
  @import "../../styles/fonts.css";

  #trailer-video-container {
    box-shadow: 0 0 50px 10px #41494d;
  }

  .screenshots > * {
    width: calc(50% - 14px);
    height: auto;
    margin: 5px;
    border: #41494d88 solid 2px;
  }

  .image {
    width: 100%;
  }

  .screenshots {
    margin: 4em 0 4em 0;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    width: 100%;
    margin: auto;
  }

  @media only screen and (max-width: 800px) {
    .screenshots > * {
      width: calc(90% - 10px);
      margin: 5px;
    }
  }

  .wrapper {
    margin: 0 calc(9.61538vw - 10.76923px) 0 calc(9.61538vw - 10.76923px);
    display: block;
  }

  ::-webkit-scrollbar {
    display: none;
  }

  .section-label {
    margin-bottom: 0.5em;
    filter: drop-shadow(0 0 20px #cdcdb6);
  }

  .screenshot-label {
    margin-bottom: 0.5em;
    display: flex;
    justify-content: center;
    text-align: center;
  }

  .screenshot-label h1 {
    width: fit-content;
  }

  .section-label.trailer {
    margin-bottom: 1.4em;
  }

  .right-section-inner {
    padding-left: 4.1666666667%;
    width: 50%;
  }

  .left-section-inner {
    margin: auto;
  }

  .regular-text p,
  .regular-text li {
    color: #b6b6a2;
  }

  .regular-text ul {
    list-style: none;
    margin-left: 0;
    padding-left: 0;
  }

  .regular-text li {
    padding-left: 2em;
    text-indent: -2em;
    margin-bottom: 0.5em;
  }

  .regular-text li:before {
    content: ">";
    font-size: 2rem;
    color: red;
    padding-right: 0.75em;
    font-family: "Monogram", monospace;
  }

  .regular-text h1 {
    color: #fffee9;
  }

  .section-item,
  .reversed-section-item {
    margin-bottom: calc(6.73077vw + 18.46154px);
    flex-direction: row;
  }

  .circle {
    display: flex;
    margin-left: auto;
    margin-right: auto;
    position: relative;
    width: 200px;
    height: 200px;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
  }

  .description-section {
    flex: 2;
  }

  .image-section {
    flex: 1;
  }

  .os-text {
    position: absolute;
    width: 80%;
    height: 100%;
    animation: rotate 13s steps(1, end) infinite;
  }

  .section-subtext {
    color: #b6b6a2;
    text-align: center;
  }

  .section-label {
    font-family: "Monogram", monospace;
    font-size: 4.5rem;
    letter-spacing: 0.1cap;
  }
  h1 {
    font-family: "Monogram", monospace;
    font-weight: normal;
    font-size: 2.2rem;
    letter-spacing: 0.1cap;
    filter: drop-shadow(0 0 5px #8e8e82);
  }

  .regular-text,
  .section-subtext {
    font-family: "Fira Code", monospace;
    font-size: 1.2rem;
  }

  .hovering-picture {
    position: absolute;
    height: 180px;
    width: auto;
    filter: drop-shadow(0 0 20px #41494d);
    animation: float 3.5s infinite ease-in-out;
  }

  @keyframes float {
    0% {
      transform: translateY(7px);
    }
    50% {
      transform: translateY(-7px);
    }
    100% {
      transform: translateY(7px);
    }
  }

  #trailer-video {
    width: 100%;
    height: 100%;
  }

  strong {
    color: red;
  }

  @media only screen and (min-width: 48em) {
    .section-item,
    .reversed-section-item {
      display: flex;
    }

    #context-description-container {
      padding-right: 4.1666666667%;
      padding-left: 0;
      height: 50%;
      margin: auto;
    }

    #context-inner-container {
      padding-right: 0;
      padding-left: 4.1666666667%;
    }

    #os-video-container {
      display: flex;
    }
  }

  @media only screen and (max-width: 48em) {
    #context-description-text {
      width: 100%;
    }

    .section-item,
    .reversed-section-item {
      display: flex;
      flex-direction: column;
      margin-bottom: calc(6.73077vw);
    }

    .title {
      margin-bottom: 5rem;
    }

    .left-section-inner,
    .right-section-inner {
      width: 100%;
      height: auto;
      padding: 0;
      display: flex;
      margin-bottom: 0;
    }

    .section-subtext {
      text-align: left;
      margin-bottom: 50px;
    }
  }

  .section-row {
    margin-bottom: 2em;
  }

  @keyframes rotate {
    0%,
    5% {
      transform: rotate(0deg);
    }
    5%,
    10% {
      transform: rotate(18deg);
    }
    10%,
    15% {
      transform: rotate(36deg);
    }
    15%,
    20% {
      transform: rotate(54deg);
    }
    20%,
    25% {
      transform: rotate(72deg);
    }
    25%,
    30% {
      transform: rotate(90deg);
    }
    30%,
    35% {
      transform: rotate(108deg);
    }
    35%,
    40% {
      transform: rotate(126deg);
    }
    40%,
    45% {
      transform: rotate(144deg);
    }
    45%,
    50% {
      transform: rotate(162deg);
    }
    50%,
    55% {
      transform: rotate(180deg);
    }
    55%,
    60% {
      transform: rotate(198deg);
    }
    60%,
    65% {
      transform: rotate(216deg);
    }
    65%,
    70% {
      transform: rotate(234deg);
    }
    70%,
    75% {
      transform: rotate(252deg);
    }
    75%,
    80% {
      transform: rotate(270deg);
    }
    80%,
    85% {
      transform: rotate(288deg);
    }
    85%,
    90% {
      transform: rotate(306deg);
    }
    90%,
    95% {
      transform: rotate(324deg);
    }
    95%,
    100% {
      transform: rotate(342deg);
    }
  }

  @media only screen and (min-width: 80em) {
    .wrapper {
      padding: 0 8.3333333333%;
    }
  }

  @media (min-width: 1360px) {
    .section-item,
    .reversed-section-item {
      margin-bottom: 50px;
    }
  }

  @media only screen and (min-width: 768px) {
    .reversed-section-item {
      flex-direction: row-reverse;
    }
  }

  @media only screen and (min-width: 1492px) {
    #context-description-text {
      width: 90%;
    }
  }
</style>
