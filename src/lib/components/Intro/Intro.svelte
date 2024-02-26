<script>
    import { onMount } from 'svelte';
    import { animationDone } from '../../../routes/stores.js';

    let animationFinished;

    animationDone.subscribe((value) => {
        animationFinished = value;
    });

    onMount(() => {
        let velocity = window.innerHeight / 40;
        let interval;
        let introPlayed = false;
        var hintIndex = 0;
        var skip = false;
        const re = new RegExp("^[a-z0-9]+$", "i");
        const hints = [
        "Enter Your Name",
        "<enter> To Cont."
        ]
        const fonts = [
        "'Open Sans', sans-serif",
        "'Wingdings', sans-serif", // Note: Wingdings may not display text as expected in HTML documents
        "'Arial', sans-serif",
        "'Black And White Picture', system-ui",
        "'DotGothic16', sans-serif"
        ];

        function updateHint() {
            document.getElementById("no-text").textContent = hints[++hintIndex % hints.length];
        }

        const hintInterval = setInterval(updateHint, 5030);

        async function transition() {
            if (window.introHandlerRef) {
                if (!skip) {
                document.removeEventListener('keydown', window.introHandlerRef);
                document.removeEventListener('input', window.introHandlerRef);
                delete window.introHandlerRef;
                }
            }
            clearInterval(hintInterval);
            const inputCursor = document.getElementsByClassName('input-cursor')[0];
            const arrow = document.getElementById("arrow");
            arrow.style.opacity = "0";
            inputCursor.remove();
            
            const textSpan = document.getElementById("text");
            textSpan.setAttribute("title", textSpan.textContent);
            textSpan.style.position = "fixed";
            textSpan.style.top = "50%";
            textSpan.style.left = "50%";
            textSpan.style.transform = "translate(-50%, -50%)";
            
            const greySpan = textSpan.cloneNode(true);
            const redSpan = textSpan.cloneNode(true);
            
            redSpan.style.color = "#FF0000";
            redSpan.style.animation = "glitch-red 1s linear infinite";
            redSpan.style.zIndex = "3";
            greySpan.style.color = "#ACA9A5";
            greySpan.style.zIndex = "3";
            greySpan.style.animation = "glitch-grey 1s linear infinite";
            
            await new Promise(r => setTimeout(r, 1500));

            textSpan.style.animation = "glitch 1s linear infinite";

            await new Promise(r => setTimeout(r, 1600));

            textSpan.parentNode.appendChild(greySpan);
            textSpan.parentNode.appendChild(redSpan);
            
            var fontIndex = 0; 
            interval = setInterval(() => {
                textSpan.style.fontFamily = fonts[fontIndex % fonts.length];
                redSpan.style.fontFamily = fonts[fontIndex % fonts.length];
                greySpan.style.fontFamily = fonts[fontIndex % fonts.length];
                ++fontIndex;
                if (++fontIndex > fonts.length * 6) {
                    const progressSpan = document.getElementById("progress-bar");
                    const introWrapperSpan = document.getElementById("intro-wrapper");
                    progressSpan.remove();
                    introWrapperSpan.innerHTML = '';
                    introWrapperSpan.remove();
                    textSpan.style.animation = "initial";
                    textSpan.style.fontFamily = "'DotGothic16', sans-serif";
                    redSpan.remove();
                    greySpan.remove();
                    animationDone.set(true);
                    clearInterval(interval);
                }
            }, 100);
        }

        function getCharacterWidth(character, element) {
            const tempElement = document.createElement('span');
            tempElement.style.visibility = 'hidden';
            tempElement.style.position = 'absolute';
            tempElement.style.font = getComputedStyle(element).font; 
            tempElement.textContent = character;
            document.body.appendChild(tempElement);
            
            const width = tempElement.offsetWidth;
            document.body.removeChild(tempElement);
            
            return width;
        }
        
        const noTextElement = document.getElementById('no-text');
        const inputCursor = document.querySelector('.input-cursor');

        const sampleText = noTextElement.textContent || noTextElement.innerText;
        const averageCharWidth = getCharacterWidth(sampleText, noTextElement) / sampleText.length;

        inputCursor.style.width = `${averageCharWidth}px`;

        window.addEventListener('resize', () => {
            if (!introPlayed)
            {
                const noTextElement = document.getElementById('no-text');
                const inputCursor = document.querySelector('.input-cursor');
                const sampleText = noTextElement.textContent || noTextElement.innerText; 
                const averageCharWidth = getCharacterWidth(sampleText, noTextElement) / sampleText.length;

                inputCursor.style.width = `${averageCharWidth}px`;
            
                const textKeySpan = document.getElementById('text');
                if (textKeySpan.textContent.length !== 0) {
                const textWidth = textKeySpan.offsetWidth;
                inputCursor.style.marginLeft = `${textWidth}px`;
                } else {
                inputCursor.style.marginLeft = "0px";
                }
            }
        });

        function updateProgressBar(x) {
            if (x) {
                const progressBar = document.getElementById("progress-bar");
                const pbComputedStyle = getComputedStyle(progressBar);
                const height = parseFloat(pbComputedStyle.getPropertyValue("--height")) || 0;
                if (height == 100) {
                    clearInterval(interval);
                    transition();
                    introPlayed = true;
                }
                if (skip) { velocity *= 1.5; }
                progressBar.style.setProperty('--height', Math.min(height + velocity/200, 100));
            } else {
                const progressBar = document.getElementById("progress-bar");
                const pbComputedStyle = getComputedStyle(progressBar)
                const height = parseFloat(pbComputedStyle.getPropertyValue("--height")) || 0;
                progressBar.style.setProperty('--height', Math.max(0, height - 3 * velocity/200));
            }
        }

        function intro(event, inputCursor, textSpan, noTextSpan, hiddenInput) {
            if (event.key === "Enter") {
                event.preventDefault();
                skip = true;
                document.removeEventListener('keydown', window.introHandlerRef);
                document.removeEventListener('input', window.introHandlerRef);
                delete window.introHandlerRef;
                if (textSpan.textContent.length == 0) {
                textSpan.textContent = "Player";
                noTextSpan.style.display = "none";
                } 
                clearInterval(interval);
                introPlayed = true;
                interval = setInterval(updateProgressBar, 5, true);
                return;
            }
            switch(event.type) {
                case 'input':
                    if (re.test(event.target.value) && textSpan.textContent.length + event.target.value.length < 16) {
                        textSpan.textContent += event.target.value;
                    }
                    event.target.value = "";
                    break;
                case 'keydown':
                    if (event.key === "Backspace")  {
                        textSpan.textContent = textSpan.textContent.slice(0, -1);
                    }
                break;
            }

            if (textSpan.textContent.length !== 0) {
                clearInterval(interval);
                interval = setInterval(updateProgressBar, 5, true);
                const textWidth = textSpan.offsetWidth;
                inputCursor.style.marginLeft = `${textWidth}px`;
            } else {
                clearInterval(interval);
                interval = setInterval(updateProgressBar, 5, false);
                inputCursor.style.marginLeft = "0px";
            }
            noTextSpan.style.display = textSpan.textContent.length !== 0 ? "none" : "block";
        }

        if (!introPlayed) {
            const inputCursor = document.querySelector('.input-cursor');
            const textSpan = document.getElementById('text');
            const noTextSpan = document.getElementById('no-text');
            const hiddenInput = document.getElementById('hidden-input');
            hiddenInput.focus();
            const introHandler = (event) => intro(event, inputCursor, textSpan, noTextSpan, hiddenInput); 
            document.addEventListener('keydown', introHandler);
            hiddenInput.addEventListener('input', introHandler);
            window.introHandlerRef = introHandler; 
        }
    });
</script>

<style>
    @import "../../../styles/components/Intro.css";

    @keyframes -global-blink {
        0% {opacity: 0;}
        40% {opacity: 0;}
        60% {opacity: 1;}
        100% {opacity: 1;}
    }

    @keyframes -global-glitch-grey {
        2%,
        64% {
            transform: translate(-42%, -56%) skew(0deg);
        }
        4%,
        60% {
            transform: translate(-52%, -50%) skew(0deg);
        }
        62% {
            transform: translate(-50%, -50%) skew(5deg);
        }
    }

    @keyframes -global-glitch-red {
        2%,
        64% {
            transform: translate(-54%, -44%) skew(0deg);
        }
        4%,
        60% {
            transform: translate(-52%, -50%) skew(0deg);
        }
        62% {
            transform: translate(-50%, -50%) skew(5deg);
        }
    }

    @keyframes -global-glitch {
        2%,
        64% {
            transform: translate(-46%, -50%) skew(0deg);
        }
        4%,
        60% {
            transform: translate(-54%, -50%) skew(0deg);
        }
        62% {
            transform: translate(-50%, -50%) skew(5deg);
        }
    }
</style>

{#if !animationFinished}
    <div id="intro-wrapper" class="wrapper">
        <form id = "text-container" on:submit|preventDefault>
        <span id="arrow">></span>
        <div id="input-container">
            <input type="text" id="hidden-input" class="real-input" maxlength="16" autocomplete="off">
            <span class="input-cursor"></span>
            <span class="input-text" id="no-text">Enter Your Name</span>
            <span class="input-text" id="text"></span>
            <span class="input-cursor"></span>
        </div>
        </form>
  </div>
  <span id="progress-bar"></span>
{/if}