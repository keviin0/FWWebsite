<script>
  import Card from './Card.svelte';

  export let category;

  const people = {
    Director: [
      { name: 'Celine Tang', role: 'as/ Designer/ Lead Writer', link: 'https://twitter.com/AMeowdy', image: '/assets/pfps/celine.avif', position: '35% 50%' }
    ],
    Producer: [
      { name: 'Lena Jeon', role: 'Producer/ Lead Artist', link: 'https://l-jeon.github.io/portfolio/', image: '/assets/pfps/lena.avif', position: '35% 50%' }
    ],
    Engineers: [
      { name: 'Mike McVey', role: 'Lead Programmer', link: 'https://mike10mcvey.wixsite.com/portfolio', image: '/assets/pfps/mike.avif', position: '35% 50%', size: '160%'},
      { name: 'Daniel Yu', role: 'Programmer', link: 'https://dyu1112.github.io/', image: '/assets/pfps/daniel.avif', position: '35% 50%' },
      { name: 'Kevin Hu', role: 'QA Lead / Web Dev', link: 'https://youtu.be/Z0B1jfVLCVA', image: '/assets/pfps/kevin_head.avif', position: '35% 50%' },
      { name: 'Julia Wang', role: 'Programmer', link: 'https://julwang.itch.io/', image: '/assets/pfps/julia.avif', position: '35% 50%' },
      { name: 'Ally Guo', role: 'Programmer', link: 'https://allyguo.wixsite.com/site', image: '/assets/pfps/ally.avif', position: '10% 70%', size:'110%' },
      { name: 'Haocheng Liu', role: 'Programmer', link: 'https://www.haochengliu.com', image: '/assets/pfps/hao.avif', position: '50% 50%', size:'105%' },
      { name: 'Jiyan Xu (Jerry)', role: 'Programmer', link: 'https://www.linkedin.com/in/jiyanxu/', image: '/assets/pfps/jerry.avif', position: '40% 90%', size: '150%' },
      { name: 'Jessica (Tobi) Xu', role: 'QA', link: 'https://www.linkedin.com/in/jessica-xu-bb3ab2237', image: '/assets/pfps/jessica.avif', position: '35% 50%' }
    ],
    Narrative: [
      { name: 'Grace Mei Ng', role: 'Writer', link: 'https://n-grace.wixsite.com/portfolio', image: '/assets/pfps/grace.avif', position: '35% 50%' },
      { name: 'Vittoria Barone', role: 'Writer', link: 'https://www.linkedin.com/in/vittoria-barone/', image: '/assets/pfps/vittoria.avif', position: '50% 50%' }
    ],
    Artists: [
      { name: 'Mingye (Jasmine) Fan', role: 'Marketing Artist/ Inventory Artist', link: 'https://fanmingye.wixsite.com/mingyefan', image: '/assets/pfps/jasmine.avif', position: '35% 50%' },
      { name: 'Michaela Chang (milkcee12)', role: 'Illustrator', link: 'https://www.instagram.com/milkcee12/', image: '/assets/pfps/michaela.avif', position: '35% 50%' },
      { name: 'Xiaodan Zhang', role: 'Artist', link: 'https://1115251618.wixsite.com/myportfolio', image: '/assets/pfps/xiaodan.avif', position: '50% 50%' }
    ],
    Audio: [
      { name: 'Johannah "johh" Chung', role: 'Lead Audio Designer/ Composer/ SFX Designer', link: 'https://lnk.bio/joh__h', image: '/assets/pfps/johh.avif', position: '35% 50%' },
      { name: 'Justin Shin', role: 'Composer', link: 'https://www.justinshinmusic.com/', image: '/assets/pfps/justin.avif', position: '50% 50%' },
      { name: 'Cryptanark', role: 'SFX', link: 'https://twitter.com/cryptanark?lang=en', image: '/assets/pfps/alex.avif', position: '45% 50%' }
    ],
    Marketing: [
      { name: 'Skylar Robinson', role: 'Lead Marketing Manager/ Assistant Producer', link: 'https://www.instagram.com/sky.robinsonn/', image: '/assets/pfps/skylar.avif', position: '40% 70%' },
      { name: 'Timothy Xayasomloth', role: 'Marketing Editor', link: '', image: '/assets/pfps/tim.avif', position: '35% 50%' }
    ]
  };
</script>

<div class="wrapper">
  {#if category in people}
    <div class="card-group-container">
      <div class="card-group">
        {#each people[category] as person}
          <div class="card">
            <Card link={person.link} image={person.image} position={person.position} name={person.name} role={person.role} size={person.size}/>
          </div>
        {/each}
      </div>
    </div>
  {/if}
</div>


<style>
  .wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px 0 20px 0;
  }

  .card-group-container {
    width: 60%; 
  }

  .card-group {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    flex-grow: 1;
  }

  @media only screen and (max-width: 632px) {
    .card-group-container {
      width: 100%;
    }
  }
</style>
