<script>
  import { onMount } from "svelte";
  import CreditsRow from "./helpers/CreditsRow.svelte";

  onMount(() => {
    const spans = document.querySelectorAll(".word-container span");

    // Store the original text content only once to avoid overwriting
    spans.forEach((span) => {
      if (!span.dataset.original) {
        span.dataset.original = span.textContent;
      }
    });

    function startRandomChange(element) {
      if (!element || element.dataset.isChanging) return;
      element.dataset.isChanging = "true";
      element.dataset.original = element.textContent;
      element.style.color = "red";
      element.textContent = Math.random() < 0.5 ? "0" : "1";
      element.dataset.intervalId = setInterval(
        () => {
          element.style.color = "red";
          element.textContent = Math.random() < 0.5 ? "0" : "1";
        },
        Math.floor(Math.random() * 25) + 100
      );
    }

    function stopRandomChange(element) {
      if (!element || !element.dataset.intervalId) return;
      clearInterval(parseInt(element.dataset.intervalId, 10));
      if (element.dataset.original !== undefined) {
        element.textContent = element.dataset.original;
        element.style.color = "#fffee9";
        delete element.dataset.isChanging;
      }
      delete element.dataset.intervalId;
    }

    function hoverGlitch(span) {
      startRandomChange(span);
      if (span.previousElementSibling) {
        startRandomChange(span.previousElementSibling);
      }
      if (span.nextElementSibling) {
        startRandomChange(span.nextElementSibling);
      }
    }

    function stopHoverGlitch(span) {
      stopRandomChange(span);
      if (span.previousElementSibling) {
        stopRandomChange(span.previousElementSibling);
      }
      if (span.nextElementSibling) {
        stopRandomChange(span.nextElementSibling);
      }
    }

    function propagateSpan(centerSpan) {
      const delayIncrement = 40;
      const centerIndex = Array.from(spans).indexOf(centerSpan);

      spans.forEach((span, index) => {
        let delay = Math.abs(index - centerIndex) * delayIncrement;

        setTimeout(() => {
          span.style.color = "red";
          span.dataset.isChanging = "true";
          span.textContent = Math.random() < 0.5 ? "0" : "1";

          setTimeout(() => {
            if (span.dataset.original !== undefined) {
              span.textContent = span.dataset.original;
              span.style.color = "#fffee9";
              delete span.dataset.isChanging;
            }
          }, 70);
        }, delay);
      });
    }

    spans.forEach((span) => {
      span.addEventListener("mousedown", () => {
        let ancestor = span.closest(".credits-container");
        let rowContainer = ancestor.querySelector(".row-container");

        // Check if the rowContainer is already open
        if (rowContainer.classList.contains("open")) {
          // Close the rowContainer by resetting its max-height
          rowContainer.style.maxHeight = null;
          rowContainer.classList.remove("open");
        } else {
          // Open the rowContainer by setting its max-height to its scrollHeight
          // Ensure all other containers are closed first
          document
            .querySelectorAll(".row-container.open")
            .forEach((openRow) => {
              openRow.style.maxHeight = null;
              openRow.classList.remove("open");
            });
          rowContainer.classList.add("open");
          rowContainer.style.maxHeight = rowContainer.scrollHeight + "px";
        }

        propagateSpan(span);
      });

      span.addEventListener("resize", () => {
        document.querySelectorAll(".row-container.open").forEach((openRow) => {
          rowContainer.style.maxHeight = rowContainer.scrollHeight + "px";
        });
      });

      span.addEventListener("mouseenter", () => hoverGlitch(span));
      span.addEventListener("mouseleave", () => stopHoverGlitch(span));
    });
  });
</script>

<div class="wrapper">
  <div class="section-label"><h1>MEET THE TEAM</h1></div>
  <div class="credits-container">
    <div class="category-container">
      <div class="word-container">
        <div class="line">
          <span>D</span>
          <span>I</span>
          <span>R</span>
          <span>E</span>
          <span>C</span>
          <span>T</span>
          <span>O</span>
          <span>R</span>
        </div>
      </div>
      <div class="row-container">
        <CreditsRow category="Director" />
      </div>
    </div>
  </div>
  <div class="credits-container">
    <div class="category-container">
      <div class="word-container">
        <div class="line">
          <span>P</span>
          <span>R</span>
          <span>O</span>
          <span>D</span>
          <span>U</span>
          <span>C</span>
          <span>E</span>
          <span>R</span>
        </div>
      </div>
      <div class="row-container">
        <CreditsRow category="Producer" />
      </div>
    </div>
  </div>
  <div class="credits-container">
    <div class="category-container">
      <div class="word-container">
        <div class="line">
          <span>E</span>
          <span>N</span>
          <span>G</span>
          <span>I</span>
          <span>N</span>
          <span>E</span>
          <span>E</span>
          <span>R</span>
        </div>
      </div>
      <div class="row-container">
        <CreditsRow category="Engineers" />
      </div>
    </div>
  </div>
  <div class="credits-container">
    <div class="category-container">
      <div class="word-container">
        <div class="line">
          <span>W</span>
          <span>R</span>
          <span>I</span>
          <span>T</span>
          <span>E</span>
          <span>R</span>
        </div>
      </div>
      <div class="row-container">
        <CreditsRow category="Narrative" />
      </div>
    </div>
  </div>
  <div class="credits-container">
    <div class="category-container">
      <div class="word-container">
        <div class="line">
          <span>A</span>
          <span>R</span>
          <span>T</span>
          <span>I</span>
          <span>S</span>
          <span>T</span>
        </div>
      </div>
      <div class="row-container">
        <CreditsRow category="Artists" />
      </div>
    </div>
  </div>
  <div class="credits-container">
    <div class="category-container">
      <div class="word-container">
        <div class="line">
          <span>A</span>
          <span>U</span>
          <span>D</span>
          <span>I</span>
          <span>O</span>
        </div>
      </div>
      <div class="row-container">
        <CreditsRow category="Audio" />
      </div>
    </div>
  </div>
  <div class="credits-container">
    <div class="category-container">
      <div class="word-container">
        <div class="line">
          <span>M</span>
          <span>A</span>
          <span>R</span>
          <span>K</span>
          <span>E</span>
          <span>T</span>
          <span>I</span>
          <span>N</span>
          <span>G</span>
        </div>
      </div>
      <div class="row-container">
        <CreditsRow category="Marketing" />
      </div>
    </div>
  </div>
</div>

<style>
  @import "../../styles/fonts.css";

  .section-label {
    font-family: "Monogram", monospace;
    letter-spacing: 0.1cap;
    width: 80%;
    margin: auto;
  }

  .section-label h1 {
    font-size: 4.5rem;
    font-weight: normal;
  }

  .category-container {
    margin-bottom: calc(1vw);
    height: 50%;
    width: 100%;
    display: flex;
    align-items: center;
    flex-direction: column;
  }

  @media only screen and (max-width: 38em) {
    .category-container {
      margin-bottom: calc(6.73077vw);
    }
  }

  :global(.row-container) {
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.25s ease-in-out;
    width: 100vw;
  }

  :global(.row-container.open) {
    margin-bottom: 20px;
  }

  .row-container {
    background-color: black;
    width: 100%;
  }

  .credits-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .word-container {
    display: block;
    width: auto;
  }

  .line {
    display: flex;
    justify-content: space-between;
    color: #fffee9;
    font-size: clamp(2vw, 6vh, 8vw);
  }

  .line span {
    font-family: "Monogram", monospace;
    font-size: 4rem;
    letter-spacing: 0.2cap;
    cursor: pointer;
    -webkit-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }
</style>
