    <script>
        import { onMount } from 'svelte';

        let willSprite = '/assets/will_sprite.svg';
        let windows = '/assets/windows_logo_white.svg';
        let trailer_video = '/assets/fwtrailer.mp4';

        let imageNamePattern = 'p';
        let imageExtension = '.png';
        let totalImages = 10;
        let images = [];

        for (let i = 1; i <= totalImages; i++) {
            images.push(`${imageNamePattern}${i}${imageExtension}`);
        }

        const clamp = (num, min, max) => Math.min(Math.max(num, min), max);

        onMount(() => {
            
            var circularText = document.querySelector('.context-text p');
            circularText.innerHTML = circularText.innerText.split('').map(
                (char, i) =>
                `<span style="transform:rotate(${i * 22.5}deg) translate(0, -100%); color: #FFFEE9; position: absolute; font-size: 2.5em; transform-origin: 0px 86px; left: 50%; font-family: DotGothic16, sans-serif;">${char}</span>`
            ).join('');

            circularText = document.querySelector('.os-text p');
            circularText.innerHTML = circularText.innerText.split('').map(
                (char, i) =>
                `<span style="transform:rotate(${i * 20}deg) translate(0, -100%); color: #FFFEE9; position: absolute; font-size: 2.5em; transform-origin: 0px 86px; left: 50%; font-family: DotGothic16, sans-serif;">${char}</span>`
            ).join('');

            addEventListener("scroll", (event) => { updateScrollRotation() });

        });

        async function updateScrollRotation() {
            var elements = document.querySelectorAll('.hovering-picture');
            var topContainer = document.querySelector('#context-container');
            var bottomContainer = document.querySelector('#os-inner-container');

            if (!elements || !topContainer || !bottomContainer) return;

            var bottomVal = bottomContainer.getBoundingClientRect().bottom;
            var topVal = topContainer.getBoundingClientRect().top;
            var scrollPercentage = clamp((window.innerHeight - topVal)/ (bottomVal - topVal), 0.6, 1.8);

            elements.forEach(function(element) {
                var translateYValue = 65 - scrollPercentage * 65;
                var rotateValue = 20 - scrollPercentage * 20; 
            
                element.style.setProperty('--translateY', `${translateYValue}px`);
                element.style.setProperty('--rotate', `${rotateValue}deg`);
            });
        }
    </script>

    <div class="wrapper">
        <div class="container">
            <div class="section-label">TRAILER</div>
            <div id="trailer-container" class="section-item">
                <div id="trailer-video-container">
                    <!-- svelte-ignore a11y-media-has-caption -->
                    <video id="trailer-video" controls>
                        <source src={trailer_video} type="video/mp4">
                    </video>
                </div>
            </div>
            <div class="section-label">ABOUT OUR GAME</div>
            <div class="section-subtext">
                Free Will is a <strong>2D psychological puzzle RPG suffering from corruption</strong>. 
                Playing this game means you accept the responsibility of cleansing Corruption from its system.
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
                        <h1>STORY</h1>
                        Control Will, a young boy who has been bedridden for most of his life, as he fights against reality-breaking monsters. <br>
                        Watch as Will tries to understand the depth of his own autonomy. <br>
                        And play out <strong>your role</strong> in cleansing the game.
                    </div>
                </div>
            </div>
            <div id="feature-container" class="section-item">
                <div id="os-inner-container" class="left-section-inner title">
                    <div class="circle">
                        <div class="os-text">
                            <p>FEATURES FEATURES </p>
                        </div>
                        <img alt="windows logo" class="hovering-picture" src={windows}/>
                    </div>
                </div>
                <div id="os-video-container" class="right-section-inner">
                    <!-- svelte-ignore a11y-media-has-caption -->
                    <div id="os-description-text"  class="regular-text">
                        <h1>FEATURES</h1>
                        > Manipulate the game's file structure through metapuzzles to influence Will's world. <br>
                        > Get to know Will--he knows you are there… <br>
                        > Cleanse the corruption. For there is no other way forward. <br>
                        > Unearth ̸i̶n̵f̷o̴r̶m̸a̷t̵i̴o̵n̸ ̸t̶h̶a̸t̷ ̶̃̕the inhabitants ̵͂̽ô̶͝f̶́ this ̄̈́h̵̐ou̅s̸e might b͑͛ȅ̴͊ ̶̂̾b̸̀̑ĕ̷͕t̷̽ter off not k̴̈́nowing. <br>
                    </div>
                </div>
            </div>
            <div class="section-label">SCREENSHOTS</div>
            <div class="screenshots">
                {#each images as image}
                    <a target="_blank" href={`/assets/screenshots/${image}`}>
                        <img class="image" src={`/assets/screenshots/${image}`} alt={image} />
                    </a>
                {/each}
            </div>
        </div>
    </div>


    <style>
        @import "../../styles/components/Trailer.css";
        @import '../../styles/fonts.css';

        #trailer-video-container {
            box-shadow: 0 0 50px 10px #41494d;
        }

        .screenshots > * {
            width: calc(50% - 10px);
            height: auto;
            margin: 5px;
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
                width: calc(50% - 10px);
                margin: 5px;
            }
        }

        
    </style>