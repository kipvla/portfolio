<script>
  import projects from "../projects";
  import Title from "../components/Title.svelte";
  import { fade } from "svelte/transition";

  let shown = false;

  const showSpecs = (id) => {
    const uls = document.querySelectorAll("ul");
    let item = uls[id];
    item.classList.toggle("shown");
  };
</script>

<div class="container-fluid justify-content-between" id="all">
  <Title />
  <br />
  <div
    class="d-flex flex-wrap justify-content-start order-1"
    id="cards"
    in:fade={{ duration: 2500 }}
  >
    {#each projects as project}
      <div class="d-flex flex-column outer my-4">
        <div class="align-self-start d-flex w-100 justify-content-between">
          <span class="align-self-start title">
            {project.title}
          </span>
          {#if window.screen.width > 768}
          <i
          class="fas fa-info-circle align-self-end"
          on:mouseenter={() => showSpecs(project.id)}
          on:mouseleave={() => showSpecs(project.id)}
        />
          {:else}
          <i
          class="fas fa-info-circle align-self-end"
          on:click={() => showSpecs(project.id)}
        />
          {/if}
        </div>
        <div class="card my-4 shadow-lg" style="width: 30rem;">
          <a href={project.url}>
            <img class="card-img-top" src={project.image} alt={project.title} />
            <div
              class="card-img-overlay d-flex flex-column justify-content-end"
            >
              <p class="card-text text-white" />
              <ul class="list-unstyled" class:shown>
                {#each project.specs as spec}
                  <li class="text-left text-white">{spec}</li>
                {/each}
              </ul>
            </div>
          </a>
        </div>
      </div>
    {/each}
  </div>
  <div class="footer">© Copyright 2021 Kip Riecken</div>
</div>

<style>
  .container-fluid {
    font-family: "Source Code Pro", monospace;
  }

  .outer {
    margin: auto;
  }

  .card {
    border: none;
    margin: auto;
    transition: transform 1s;
  }

  .card:active {
    transform: scale(0.96);
    transition: transform 0.2s;
  }

  .card:hover {
    cursor: pointer;
    transform: scale(1.02);
    transition: transform 1s;
  }

  .card div ul {
    visibility: hidden;
    opacity: 0;
    transition: visibility 0.5s, opacity 1s, background-color 1s;
  }

  .card:hover div ul {
    visibility: visible;
    background-color: rgb(0, 0, 0, 0.5);
    opacity: 1;
    transition: opacity 1s, background-color 1s;
  }

  .shown {
    visibility: visible !important;
    background-color: rgb(0, 0, 0, 0.5);
    opacity: 1 !important;
    transition: opacity 1s, background-color 1s;
  }

  #cards {
    align-items: flex-start;
    overflow: visible;
  }

  ul {
    max-width: fit-content;
    border-radius: 5px;
    padding: 0.5rem;
    max-height: inherit;
    overflow: scroll;
    line-height: 1.3;
    font-size: 0.8rem;
  }

  .title {
    font-size: 0.9rem;
  }

  @media only screen and (max-width: 768px) {
    .card {
      max-width: 90vw;
    }
  }
</style>
