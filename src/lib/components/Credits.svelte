<script>
    import { onMount } from 'svelte';
    import CreditsRow from './helpers/CreditsRow.svelte';

    onMount(() => {
        const spans = document.querySelectorAll('.word-container span');

        // Store the original text content only once to avoid overwriting
        spans.forEach(span => {
            if (!span.dataset.original) {
                span.dataset.original = span.textContent;
            }
        });

        function startRandomChange(element) {
            if (!element || element.dataset.isChanging) return;
            element.dataset.isChanging = 'true';
            element.dataset.original = element.textContent;
            element.style.color = "red";
            element.textContent = Math.random() < 0.5 ? '0' : '1';
            element.dataset.intervalId = setInterval(() => {
                element.style.color = "red";
                element.textContent = Math.random() < 0.5 ? '0' : '1';
            }, Math.floor(Math.random() * 25) + 100);
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
                    span.dataset.isChanging = 'true';
                    span.textContent = Math.random() < 0.5 ? '0' : '1';

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

        spans.forEach(span => {
            span.addEventListener('click', () => {
                let ancestor = span.closest('.credits-container');
                let rowContainer = ancestor.querySelector('.row-container');

                // Toggle the open class for rowContainer
                if (rowContainer.classList.contains('open')) {
                    rowContainer.classList.remove('open');
                } else {
                    document.querySelectorAll('.row-container.open').forEach(openRow => {
                        openRow.classList.remove('open');
                    });
                    rowContainer.classList.add('open');
                }

                propagateSpan(span);
            });

            span.addEventListener('mouseenter', () => hoverGlitch(span));
            span.addEventListener('mouseleave', () => stopHoverGlitch(span));
        });
    });
</script>


<div class="wrapper">
    <div class="section-label">Meet the team</div>
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
                <CreditsRow class="credits-row"/>
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
                <CreditsRow class="credits-row"/>
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
                    <span>S</span>
                </div>
            </div>
            <div class="row-container">
                <CreditsRow class="credits-row"/>
            </div>
        </div>
    </div>
    <div class="credits-container">
        <div class="category-container">
            <div class="word-container">
                <div class="line">
                    <span>N</span>
                    <span>A</span>
                    <span>R</span>
                    <span>R</span>
                    <span>A</span>
                    <span>T</span>
                    <span>I</span>
                    <span>V</span>
                    <span>E</span>
                </div>
            </div>
            <div class="row-container">
                <CreditsRow class="credits-row"/>
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
                    <span>S</span>
                </div>
            </div>
            <div class="row-container">
                <CreditsRow class="credits-row"/>
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
                <CreditsRow class="credits-row"/>
            </div>
        </div>
    </div>
</div>


<style>
    @import '../../styles/fonts.css';

    .section-label {
        margin-bottom: calc(3.84615vw + 25px);
        margin-top: calc(3.84615vw + 57.69231px);
        font-family: "DotGothic16", sans-serif;
        color: #fffee9;
        width: 100%;
        text-align: center;
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
        max-height: calc(42vh + 40px); /* Example value */
    }

    .wrapper {
        height: 100vh; /* This ensures that the wrapper takes the full viewport height */
    }

    .row-container {
        background-color: #41494D;
        width: 100%;
    }

    .credits-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center; /* This will center the word-container vertically */
    }

    .word-container {
        display: block;
        width: auto;
    }

    .line {
        display: flex;
        justify-content: space-between;
        color: #fffee9;
        font-size: clamp(2vw, 8vh, 8vw);
    }

    .line span {
        font-family: 'Apple', sans-serif;
        cursor: pointer;
    }
</style>