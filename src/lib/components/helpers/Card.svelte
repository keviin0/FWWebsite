<script>
  export let link;
  export let image;
  export let position;
  export let name;
  export let role;
  export let size;

  let x = 0;
  let y = 0;
  let scale = 1;
  let zIndex = 0;

  function handleMouseMove(event) {
    const cardRect = event.currentTarget.getBoundingClientRect();
    const centerX = cardRect.width / 4;
    const centerY = cardRect.height / 4;
    x = (event.clientX - cardRect.left - centerX - 80) * 0.1;
    y = (event.clientY - cardRect.top - centerY) * 0.1;
    scale = 1.05;
    zIndex = 1;
  }

  function handleMouseLeave() {
    x = 0;
    y = 0;
    scale = 1;
    zIndex = 0;
  }
</script>

<div class="card" on:mousemove={handleMouseMove} on:mouseleave={handleMouseLeave} role="button" tabindex="0" style={`transform: translate(${x}px, ${y}px) scale(${scale}); z-index: ${zIndex};`}>
  <a target="_blank" href={link} style={`background-image: url('${image}'); background-position: ${position}; background-size: ${size};`}>
    <div class="person-info">
      <div class="person-name">{name}</div>
      <div class="person-role">{role}</div>
    </div>
  </a>
</div>

<style>
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
    transform: translateY(-55%);
    opacity: 1;
  }

  .card {
    aspect-ratio: 5 / 7;
    width: 20vmin;
    border: #43474b solid 2px;
    margin: 20px;
    transition: transform 0.1s ease-out;
    cursor: pointer;
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .person-info {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;
    position: absolute;
    width: 100%;
    height: 60%;
  }

  .person-name, .person-role {
    font-family: 'Monogram', monospace;
    font-size: 1.3rem;
    letter-spacing: 0.1cap;
    color: #fffee9;
    width: 90%;
    text-align: center;
  }

  .person-role {
    margin-bottom: 1.2em;
    font-size: 1rem;
  }

  @media only screen and (max-width: 632px) {
    .card {
      width: 35vmin;
      margin: 10px 10px 10px 10px;
    }

    .person-info {
      height: 40%;
    }

    .person-role {
      font-size: 0.5rem;
    }
  }
</style>
