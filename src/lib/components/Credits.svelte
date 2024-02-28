<script>
    import { onMount } from 'svelte';
    import CreditsRow from './helpers/CreditsRow.svelte'

    let showComponent = false;
    
    onMount(() => {
        const spans = document.querySelectorAll('.word-container span');

        function startRandomChange(element) {
            element.style.color = "red";
            if (!element) return;
            element.dataset.original = element.textContent;
            const interval = Math.floor(Math.random() * 25) + 100; // Random interval between 100ms and 300ms
            element.dataset.intervalId = setInterval(() => {
                element.textContent = Math.random() < 0.5 ? '0' : '1';
            }, interval);
        }

        function stopRandomChange(element) {
            if (!element || !element.dataset.intervalId) return;
            element.style.color = "#fffee9";
            clearInterval(parseInt(element.dataset.intervalId));
            if (element.dataset.original !== undefined) {
                element.textContent = element.dataset.original;
                delete element.dataset.original;
            }
            delete element.dataset.intervalId;
        }

        spans.forEach(span => {
            span.addEventListener('click', () => {
                showComponent = !showComponent;
                document.querySelectorAll('.row-container.open').forEach(openRow => {
                    openRow.classList.toggle('open');
                });

                const creditsRow = container.querySelector('.row-container');
                if (creditsRow) {
                    creditsRow.classList.toggle('open');
                }
            });

            span.addEventListener('mouseenter', () => {
                startRandomChange(span);
                if (span.previousElementSibling != null)
                {
                    startRandomChange(span.previousElementSibling);
                }
                if (span.nextElementSibling != null)
                {
                    startRandomChange(span.nextElementSibling);
                }
            });

            span.addEventListener('mouseleave', () => {
                stopRandomChange(span);
                if (span.previousElementSibling != null)
                {
                    stopRandomChange(span.previousElementSibling);
                }
                if (span.nextElementSibling != null)
                {
                    stopRandomChange(span.nextElementSibling);
                }
            });
        });
    });
</script>

<div class="wrapper">
    <div class="credits-container">
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

<style>
    @import '../../styles/fonts.css';

    .row-container {
        max-height: 0;
        overflow: hidden;
        transition: max-height 0.5s ease-in-out;
    }

    .row-container.open {
        max-height: none; /* Adjust based on the content's natural height */
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
        width: 512px;
    }

    .line {
        display: flex;
        justify-content: space-between;
        color: #fffee9;
        font-size: 4em;
    }

    .line span {
        font-family: 'Apple', sans-serif;
        cursor: pointer;
    }
</style>