    <script>
        import { onMount } from 'svelte';

        let tv = '/assets/TV.svg';
        let willSprite = '/assets/will_sprite.svg';
        let windows = '/assets/windows_logo_white.svg';
        let trailer_video = '/assets/FWTrailer_03.mp4';

        const clamp = (num, min, max) => Math.min(Math.max(num, min), max);

        onMount(() => {
            var circularText = document.querySelector('.circular-text p');
            circularText.innerHTML = circularText.innerText.split('').map(
                (char, i) =>
                `<span style="transform:rotate(${i * 22.5}deg) translate(0, -100%); color: #FFFEE9; position: absolute; font-size: 2.5em; transform-origin: 0px 86px; left: 50%; font-family: DotGothic16, sans-serif;">${char}</span>`
            ).join('');
            
            circularText = document.querySelector('.context-text p');
            circularText.innerHTML = circularText.innerText.split('').map(
                (char, i) =>
                `<span style="transform:rotate(${i * 22.5}deg) translate(0, -100%); color: #FFFEE9; position: absolute; font-size: 2.5em; transform-origin: 0px 86px; left: 50%; font-family: DotGothic16, sans-serif;">${char}</span>`
            ).join('');

            circularText = document.querySelector('.os-text p');
            circularText.innerHTML = circularText.innerText.split('').map(
                (char, i) =>
                `<span style="transform:rotate(${i * 21.18}deg) translate(0, -100%); color: #FFFEE9; position: absolute; font-size: 2.5em; transform-origin: 0px 86px; left: 50%; font-family: DotGothic16, sans-serif;">${char}</span>`
            ).join('');

            addEventListener("scroll", (event) => { updateScrollRotation() });

        });

        async function updateScrollRotation() {
            var elements = document.querySelectorAll('.hovering-picture');
            var container = document.querySelector('.container');

            if (!elements || !container) return;

            var bottomVal = container.getBoundingClientRect().bottom;
            var topVal = container.getBoundingClientRect().top;
            var scrollPercentage = clamp((window.innerHeight - topVal)/ (bottomVal - topVal), 0, 4);
            console.log(scrollPercentage);

            // Apply the transformation to each hovering-picture element
            elements.forEach(function(element) {
                var translateYValue = 100 - scrollPercentage * 100;
                var rotateValue = 20 - scrollPercentage * 20; 
            
                element.style.setProperty('--translateY', `${translateYValue}px`);
                element.style.setProperty('--rotate', `${rotateValue}deg`);
            });
        }
    </script>

    <div class="wrapper">
        <div class="container">
            <div class="section-label">About our game</div>
            <div id="trailer-container" class="section-item">
                <div id="trailer-inner-container" class="left-section-inner title">
                    <div class="circle">
                        <div class="circular-text">
                            <p>TRAILER TRAILER </p>
                        </div>
                        <img alt="tv" class="hovering-picture" src={tv}/>
                    </div>
                </div>
                <div id="trailer-video-container" class="right-section-inner">
                    <!-- svelte-ignore a11y-media-has-caption -->
                    <video id="trailer-video" controls>
                        <source src={trailer_video} type="video/mp4">
                    </video>
                </div>
            </div>
            <div id="context-container" class="reversed-section-item">
                <div id="context-inner-container" class="left-section-inner title">
                    <div class="circle">
                        <div class="context-text">
                            <p>CONTEXT CONTEXT </p>
                        </div>
                        <img id="will-sprite" alt="will sprite" class="hovering-picture" src={willSprite}/>
                    </div>
                </div>
                <div id="context-description-container" class="right-section-inner">
                    <div id="context-description-text"  class="regular-text">
                        <strong>Free Will</strong> is a <strong>2D psychological puzzle RPG</strong> where players tackle corruption within the game's system. As Will, a chronically ill boy, players face reality-distorting enemies and delve into the game's code to expose hidden truths and cleanse corruption, confronting challenges that question the nature of choice and knowledge within a mysterious, deteriorating digital world.
                    </div>
                </div>
            </div>
            <div class="section-item">
                <div id="os-inner-container" class="left-section-inner title">
                    <div class="circle">
                        <div class="os-text">
                            <p>OPERATING SYSTEM </p>
                        </div>
                        <img alt="windows logo" class="hovering-picture" src={windows}/>
                    </div>
                </div>
                <div id="os-video-container" class="right-section-inner">
                    <!-- svelte-ignore a11y-media-has-caption -->
                    <div id="os-description-text"  class="regular-text">
                        <strong>WINDOWS ONLY</strong>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div id="filler">

    </div>

    <style>
        @import "../../styles/Trailer.css";

    </style>