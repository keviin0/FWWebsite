<script>
    export let category;
    import { onMount } from 'svelte';

    onMount(() => {
        document.querySelectorAll('.card').forEach(card => {
            card.addEventListener('mousemove', function(e) {
                const rect = this.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                const centerX = rect.width/4;
                const centerY = rect.height / 4;

                const deltaX = (x - centerX - 80) * 0.1;
                const deltaY = (y - centerY) * 0.1;

                this.style.transform = `translate(${deltaX}px, ${deltaY}px) scale(1.05)`;
                this.style.zIndex = "1";
            });

            card.addEventListener('mouseleave', function() {
                this.style.transform = 'translate(0%, 0%)';
                this.style.zIndex = "0";
            });
        });
    });
</script>


<div class='wrapper'> 
    {#if category === "Director"}
    <div class="card-group-container">
        <div class='card-group'>
            <div class="card">
                <a target="_blank" href="https://twitter.com/AMeowdy" style="background-image: url('/assets/pfps/celine.png'); background-position: 35% 50%">
                <div class="person-info">
                    <div class="person-name">
                        Celine Tang
                    </div>
                    <div class="person-role">
                        Director/ Designer/ Lead Writer
                    </div>
                </div>
            </div>
        </div>
    </div>
    {/if}
    {#if category === "Producer"}
    <div class="card-group-container">
        <div class='card-group'>
            <div class="card">
                <a target="_blank" href="https://l-jeon.github.io/portfolio/" style="background-image: url('/assets/pfps/lena.png'); background-position: 35% 50%">
                <div class="person-info">
                    <div class="person-name">
                        Lena Jeon
                    </div>
                    <div class="person-role">
                        Producer/ Lead Artist
                    </div>
                </div>
            </div>
        </div>
    </div>
    {/if}
    {#if category === "Engineers"}
    <div class="card-group-container">
        <div class='card-group'>
            <div class="card">
                <a target="_blank" href="https://mike10mcvey.wixsite.com/portfolio" style="background-image: url('/assets/pfps/mike.jpg'); background-position: 35% 50%; background-size: 160%">
                <div class="person-info">
                    <div class="person-name">
                        Mike McVey
                    </div>
                    <div class="person-role">
                        Lead Programmer
                    </div>
                </div>
            </div>
            <div class="card">
                <a target="_blank" href="https://dyu1112.github.io/" style="background-image: url('/assets/pfps/daniel.png'); background-position: 35% 50%">
                <div class="person-info">
                    <div class="person-name">
                        Daniel Yu
                    </div>
                    <div class="person-role">
                        Programmer
                    </div>
                </div>
            </div>
            <div class="card">
                <a target="_blank" href="https://youtu.be/Z0B1jfVLCVA" style="background-image: url('/assets/pfps/kevin_head.jpeg'); background-position: 35% 50%">
                <div class="person-info">
                    <div class="person-name">
                        Kevin Hu
                    </div>
                    <div class="person-role">
                        QA Lead / Web Dev
                    </div>
                </div>
            </div>
            <div class="card">
                <a target="_blank" href="https://julwang.itch.io/" style="background-image: url('/assets/pfps/julia.jpg'); background-position: 35% 50%">
                <div class="person-info">
                    <div class="person-name">
                        Julia Wang
                    </div>
                    <div class="person-role">
                        Programmer
                    </div>
                </div>
            </div>
            <div class="card">
                <a target="_blank" href="https://allyguo.wixsite.com/site" style="background-image: url('/assets/pfps/ally.jpg'); background-position: 10% 70%; background-size: 110%">
                <div class="person-info">
                    <div class="person-name">
                        Ally Guo
                    </div>
                    <div class="person-role">
                        Programmer
                    </div>
                </div>
            </div>
            <div class="card">
                <a target="_blank" href="https://www.haochengliu.com" style="background-image: url('/assets/pfps/hao.png'); background-position: 35% 50%; background-size: 110%">
                <div class="person-info">
                    <div class="person-name">
                        Haocheng Liu
                    </div>
                    <div class="person-role">
                        Programmer
                    </div>
                </div>
            </div>
            <div class="card">
                <a target="_blank" href>
                <div class="person-info">
                    <div class="person-name">
                        Jiyan (Jerry) Xu
                    </div>
                    <div class="person-role">
                        Programmer
                    </div>
                </div>
            </div>
            <div class="card">
                <a target="_blank" href>
                <div class="person-info">
                    <div class="person-name">
                        Jessica (Tobi) Xu
                    </div>
                    <div class="person-role">
                        QA
                    </div>
                </div>
            </div>
        </div>
    </div>
    {/if}
    {#if category === "Narrative"}
    <div class="card-group-container">
        <div class='card-group'>
            <div class="card">
                <a target="_blank" href="https://n-grace.wixsite.com/portfolio" style="background-image: url('/assets/pfps/grace.jpeg'); background-position: 35% 50%">
                <div class="person-info">
                    <div class="person-name">
                        Grace Mei Ng
                    </div>
                    <div class="person-role">
                        Writer
                    </div>
                </div>
            </div>
            <div class="card">
                <a target="_blank" href>
                <div class="person-info">
                    <div class="person-name">
                        Vittoria Barone
                    </div>
                    <div class="person-role">
                        Writer
                    </div>
                </div>
            </div>
        </div>
    </div>
    {/if}
    {#if category === "Artists"}
    <div class="card-group-container">
        <div class='card-group'>
            <div class="card">
                <a target="_blank" href="https://fanmingye.wixsite.com/mingyefan" style="background-image: url('/assets/pfps/jasmine.png'); background-position: 35% 50%">
                <div class="person-info">
                    <div class="person-name">
                        Mingye (Jasmine) Fan
                    </div>
                    <div class="person-role">
                        Marketing Artist/ Inventory Artist
                    </div>
                </div>
            </div>
            <div class="card">
                <a target="_blank" href="https://www.instagram.com/milkcee12/" style="background-image: url('/assets/pfps/icemasterx.jpg'); background-position: 35% 50%">
                <div class="person-info">
                    <div class="person-name">
                        Michaela Chang (milkcee12)
                    </div>
                    <div class="person-role">
                        Illustrator
                    </div>
                </div>
            </div>
            <div class="card">
                <a target="_blank" href>
                <div class="person-info">
                    <div class="person-name">
                        Xiaodan Zhang
                    </div>
                    <div class="person-role">
                        Artists
                    </div>
                </div>
            </div>
        </div>
    </div>
    {/if}
    {#if category === "Audio"}
    <div class="card-group-container">
        <div class='card-group'>
            <div class="card">
                <a target="_blank" href="https://lnk.bio/joh__h" style="background-image: url('/assets/pfps/johh.jpg'); background-position: 35% 50%">
                <div class="person-info">
                    <div class="person-name">
                        Johannah "johh" Chung
                    </div>
                    <div class="person-role">
                        Lead Audio Designer/ Composer/ SFX Designer
                    </div>
                </div>
            </div>
            <div class="card">
                <a target="_blank" href="https://www.justinshinmusic.com/" style="background-image: url('/assets/pfps/justin.jpg'); background-position: 50% 50%">
                <div class="person-info">
                    <div class="person-name">
                        Justin Shin
                    </div>
                    <div class="person-role">
                        Composer
                    </div>
                </div>
            </div>
            <div class="card">
                <a target="_blank" href>
                <div class="person-info">
                    <div class="person-name">
                        Cryptanark
                    </div>
                    <div class="person-role">
                        SFX
                    </div>
                </div>
            </div>
        </div>
    </div>
    {/if}
    {#if category === "Marketing"}
    <div class="card-group-container">
        <div class='card-group'>
            <div class="card">
                <a target="_blank" href="https://www.instagram.com/sky.robinsonn/" style="background-image: url('/assets/pfps/skylar.jpeg'); background-position: 35% 50%">
                <div class="person-info">
                    <div class="person-name">
                        Skylar Robinson
                    </div>
                    <div class="person-role">
                        Lead Marketing Manager/ Assistant Producer
                    </div>
                </div>
            </div>
            <div class="card">
                <a target="_blank" href>
                <div class="person-info">
                    <div class="person-name">
                        Timothy Xayasomloth
                    </div>
                    <div class="person-role">
                        Marketing Writer
                    </div>
                </div>
            </div>
        </div>
    </div>
    {/if}
</div>

<style>
    @import "../../../styles/components/CreditsRow.css";
</style>