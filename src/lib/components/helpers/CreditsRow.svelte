<script>
  export let category;
  import { onMount } from "svelte";

  onMount(() => {
    document.querySelectorAll(".card").forEach((card) => {
      card.addEventListener("mousemove", function (e) {
        const rect = this.getBoundingClientRect();
        const x = e.clientX - rect.left;
        const y = e.clientY - rect.top;
        const centerX = rect.width / 4;
        const centerY = rect.height / 4;
        const deltaX = (x - centerX - 80) * 0.1;
        const deltaY = (y - centerY) * 0.1;
        this.style.transform = `translate(${deltaX}px, ${deltaY}px) scale(1.05)`;
        this.style.zIndex = "1";
      });
      card.addEventListener("mouseleave", function () {
        this.style.transform = "translate(0%, 0%)";
        this.style.zIndex = "0";
      });
    });
  });
</script>

<div class="wrapper">
  {#if category === "Director"}
    <div class="card-group-container">
      <div class="card-group">
        <div class="card">
          <a
            target="_blank"
            href="https://twitter.com/AMeowdy"
            style="background-image: url('/assets/pfps/celine.png'); background-position: 35% 50%">
            <div class="person-info">
              <div class="person-name">Celine Tang</div>
              <div class="person-role">Director/ Designer/ Lead Writer</div>
            </div>
          </a>
        </div>
      </div>
    </div>
  {/if}
  {#if category === "Producer"}
    <div class="card-group-container">
      <div class="card-group">
        <div class="card">
          <a
            target="_blank"
            href="https://l-jeon.github.io/portfolio/"
            style="background-image: url('/assets/pfps/lena.png'); background-position: 35% 50%">
            <div class="person-info">
              <div class="person-name">Lena Jeon</div>
              <div class="person-role">Producer/ Lead Artist</div>
            </div>
          </a>
        </div>
      </div>
    </div>
  {/if}
  {#if category === "Engineers"}
    <div class="card-group-container">
      <div class="card-group">
        <div class="card">
          <a
            target="_blank"
            href="https://mike10mcvey.wixsite.com/portfolio"
            style="background-image: url('/assets/pfps/mike.jpg'); background-position: 35% 50%; background-size: 160%">
            <div class="person-info">
              <div class="person-name">Mike McVey</div>
              <div class="person-role">Lead Programmer</div>
            </div>
          </a>
        </div>
        <div class="card">
          <a
            target="_blank"
            href="https://dyu1112.github.io/"
            style="background-image: url('/assets/pfps/daniel.png'); background-position: 35% 50%">
            <div class="person-info">
              <div class="person-name">Daniel Yu</div>
              <div class="person-role">Programmer</div>
            </div>
          </a>
        </div>
        <div class="card">
          <a
            target="_blank"
            href="https://youtu.be/Z0B1jfVLCVA"
            style="background-image: url('/assets/pfps/kevin_head.jpeg'); background-position: 35% 50%">
            <div class="person-info">
              <div class="person-name">Kevin Hu</div>
              <div class="person-role">QA Lead / Web Dev</div>
            </div>
          </a>
        </div>
        <div class="card">
          <a
            target="_blank"
            href="https://julwang.itch.io/"
            style="background-image: url('/assets/pfps/julia.jpg'); background-position: 35% 50%">
            <div class="person-info">
              <div class="person-name">Julia Wang</div>
              <div class="person-role">Programmer</div>
            </div>
          </a>
        </div>
        <div class="card">
          <a
            target="_blank"
            href="https://allyguo.wixsite.com/site"
            style="background-image: url('/assets/pfps/ally.jpg'); background-position: 10% 70%; background-size: 110%">
            <div class="person-info">
              <div class="person-name">Ally Guo</div>
              <div class="person-role">Programmer</div>
            </div>
          </a>
        </div>
        <div class="card">
          <a
            target="_blank"
            href="https://www.haochengliu.com"
            style="background-image: url('/assets/pfps/hao.png'); background-position: 50% 50%; background-size: 105%">
            <div class="person-info">
              <div class="person-name">Haocheng Liu</div>
              <div class="person-role">Programmer</div>
            </div>
          </a>
        </div>
        <div class="card">
          <a
            target="_blank"
            href="https://www.linkedin.com/in/jiyanxu/"
            style="background-image: url('/assets/pfps/jerry.jpg'); background-position: 40% 90%; background-size: 150%">
            <div class="person-info">
              <div class="person-name">Jiyan Xu (Jerry)</div>
              <div class="person-role">Programmer</div>
            </div>
          </a>
        </div>
        <div class="card">
          <a
            target="_blank"
            href
            style="background-image: url('/assets/pfps/jessica.jpg')">
            <div class="person-info">
              <div class="person-name">Jessica (Tobi) Xu</div>
              <div class="person-role">QA</div>
            </div>
          </a>
        </div>
      </div>
    </div>
  {/if}
  {#if category === "Narrative"}
    <div class="card-group-container">
      <div class="card-group">
        <div class="card">
          <a
            target="_blank"
            href="https://n-grace.wixsite.com/portfolio"
            style="background-image: url('/assets/pfps/grace.jpeg'); background-position: 35% 50%">
            <div class="person-info">
              <div class="person-name">Grace Mei Ng</div>
              <div class="person-role">Writer</div>
            </div>
          </a>
        </div>
        <div class="card">
          <a
            target="_blank"
            href="https://www.linkedin.com/in/vittoria-barone/"
            style="background-image: url('/assets/pfps/vittoria.png'); background-position: 50% 50%">
            <div class="person-info">
              <div class="person-name">Vittoria Barone</div>
              <div class="person-role">Writer</div>
            </div>
          </a>
        </div>
      </div>
    </div>
  {/if}
  {#if category === "Artists"}
    <div class="card-group-container">
      <div class="card-group">
        <div class="card">
          <a
            target="_blank"
            href="https://fanmingye.wixsite.com/mingyefan"
            style="background-image: url('/assets/pfps/jasmine.png'); background-position: 35% 50%">
            <div class="person-info">
              <div class="person-name">Mingye (Jasmine) Fan</div>
              <div class="person-role">Marketing Artist/ Inventory Artist</div>
            </div>
          </a>
        </div>
        <div class="card">
          <a
            target="_blank"
            href="https://www.instagram.com/milkcee12/"
            style="background-image: url('/assets/pfps/michaela.jpg'); background-position: 35% 50%">
            <div class="person-info">
              <div class="person-name">Michaela Chang (milkcee12)</div>
              <div class="person-role">Illustrator</div>
            </div>
          </a>
        </div>
        <div class="card">
          <a
            target="_blank"
            href="https://1115251618.wixsite.com/myportfolio"
            style="background-image: url('/assets/pfps/xiaodan.png'); background-position: 50% 50%">
            <div class="person-info">
              <div class="person-name">Xiaodan Zhang</div>
              <div class="person-role">Artist</div>
            </div>
          </a>
        </div>
      </div>
    </div>
  {/if}
  {#if category === "Audio"}
    <div class="card-group-container">
      <div class="card-group">
        <div class="card">
          <a
            target="_blank"
            href="https://lnk.bio/joh__h"
            style="background-image: url('/assets/pfps/johh.jpg'); background-position: 35% 50%">
            <div class="person-info">
              <div class="person-name">Johannah "johh" Chung</div>
              <div class="person-role">
                Lead Audio Designer/ Composer/ SFX Designer
              </div>
            </div>
          </a>
        </div>
        <div class="card">
          <a
            target="_blank"
            href="https://www.justinshinmusic.com/"
            style="background-image: url('/assets/pfps/justin.jpg'); background-position: 50% 50%">
            <div class="person-info">
              <div class="person-name">Justin Shin</div>
              <div class="person-role">Composer</div>
            </div>
          </a>
        </div>
        <div class="card">
          <a
            target="_blank"
            href="https://twitter.com/cryptanark?lang=en"
            style="background-image: url('/assets/pfps/alex.png'); background-position: 45% 50%">
            <div class="person-info">
              <div class="person-name">Cryptanark</div>
              <div class="person-role">SFX</div>
            </div>
          </a>
        </div>
      </div>
    </div>
  {/if}
  {#if category === "Marketing"}
    <div class="card-group-container">
      <div class="card-group">
        <div class="card">
          <a
            target="_blank"
            href="https://www.instagram.com/sky.robinsonn/"
            style="background-image: url('/assets/pfps/skylar.jpeg'); background-position: 40% 70%">
            <div class="person-info">
              <div class="person-name">Skylar Robinson</div>
              <div class="person-role">
                Lead Marketing Manager/ Assistant Producer
              </div>
            </div>
          </a>
        </div>
        <div class="card">
          <a
            href
            target="_blank"
            style="background-image: url('/assets/pfps/tim.jpg'); background-position: 35% 50%">
            <div class="person-info">
              <div class="person-name">Timothy Xayasomloth</div>
              <div class="person-role">Marketing Editor</div>
            </div>
          </a>
        </div>
      </div>
    </div>
  {/if}
</div>

<style>
  .person-info {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;
    position: absolute;
    width: 100%;
    height: 60%;
  }

  .person-name {
    font-family: "Monogram", monospace;
    font-size: 1.3rem;
    letter-spacing: 0.1cap;
    color: #fffee9;
    width: 90%;
    text-align: center;
  }

  .person-role {
    font-family: "Monogram", monospace;
    letter-spacing: 0.1cap;
    font-size: 1rem;
    color: #fffee9;
    width: 90%;
    margin-bottom: 1.2em;
  }

  .card a {
    display: flex;
    align-items: flex-end;
    background-size: cover;
    background-repeat: no-repeat;
    width: 100%;
    height: 100%;
    transform-origin: 50% 50%;
    transition: all 0.4s;
  }

  .card a::before {
    content: "";
    position: absolute;
    display: block;
    width: 100%;
    height: 100%;
    bottom: 0;
    transition: all 0.4s;
    background: linear-gradient(
      to top,
      rgba(0, 0, 0, 0.9) 0%,
      rgba(0, 0, 0, 0.8) 12%,
      rgba(0, 0, 0, 0.0) 60%,
      transparent 100%
    );
  }

  .card a .person-info {
    transform-origin: 50% 20%;
    transition: all 0.4s;
  }

  .card:hover a .person-info {
    transform: scale(0.8) translateY(-55%);
    opacity: 1;
  }

  .card:hover a {
    transform: scale(1.3);
  }

  .card:hover a::before {
    background-color: rgba(0,0,0,0.6);
  }

  .card {
    aspect-ratio: 5 / 7;
    width: 20vmin;
    border: #43474b solid 2px;
    margin: 20px 20px 20px 20px;
    transition: transform 0.1s ease-out;
    cursor: pointer;
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .card-group-container {
    width: 60%;
  }

  @media only screen and (max-width: 1390px) {
    .card {
      width: 20vmin;
      margin: 10px 10px 10px 10px;
    }

    .card-group-container {
      width: 80%;
    }
  }

  @media only screen and (max-width: 632px) {
    .card {
      width: 35vmin;
      margin: 10px 10px 10px 10px;
    }

    .card-group-container {
      width: 100%;
    }

    .person-info {
      height: 40%;
    }

    .person-role {
      font-size: 0.5rem;
    }
  }

  .card-group {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    flex-grow: 1;
  }

  .wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px 0 20px 0;
  }
</style>
