<script>
  import projects from "../projects";
  import Title from "../components/Title.svelte";
  import { fade } from "svelte/transition";
  import { init } from "emailjs-com";

  let component;
  let props;

  let shown = false;
  let color = "black";

  const colorChange = () => {
    if (color === "black") {
      color = "white";
      return;
    }
    color = "black";
  };

  const devMode = () => {
    const titles = document.querySelectorAll(".title");
    const infos = document.querySelectorAll(".fa-info-circle");
    const all = document.querySelector("#all");
    const btn = document.querySelector(".btn");
    const footer = document.querySelector(".footer");
    titles.forEach((title) => title.classList.toggle("text-white"));
    infos.forEach((info) => info.classList.toggle("text-white"));
    all.classList.toggle("bg-white");
    footer.classList.toggle("text-white");
    btn.classList.toggle("text-white");
    btn.classList.toggle("bg-secondary");
    colorChange();
  };

  const showSpecs = (id) => {
    const uls = document.querySelectorAll("ul");
    let item = uls[id];
    item.classList.toggle("shown");
  };


  window.onload = function () {
    init("user_L3ByXl8YCtcujXmSA2V60");
    document
      .getElementById("contact-form")
      .addEventListener("submit", function (event) {
        event.preventDefault();
        // generate a five digit number for the contact_number variable
        this.contact_number.value = (Math.random() * 100000) | 0;
        // these IDs from the previous steps
        emailjs.sendForm("contact_service", "contact_form", this).then(
          function () {
            console.log("SUCCESS!");
          },
          function (error) {
            console.log("FAILED...", error);
          }
        );
      });
  };
</script>

<div class="container-fluid justify-content-between bg-white" id="all">
  <div class="d-flex flex-column align-items-start">
    <Title {color} />
    <button class="btn btn-sm mt-4" on:click={() => devMode()}>
      click me
      <i class="fas fa-code" />
    </button>
  </div>
  <br />
  <div
    class="d-flex flex-wrap justify-content-start order-1"
    id="cards"
    in:fade={{ duration: 2500 }}
  >
    {#each projects as project}
      <div class="d-flex flex-column outer my-5">
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
  <!-- <form id="contact-form">
    <div class="form-group">
      <input type="hidden" name="contact_number" />
      <label for="user_name">Name</label>
      <input type="text" class="form-control" name="user_name" />
    </div>
    <div class="form-group">
      <label for="user_email">Email</label>
      <input type="email" class="form-control" name="user_email" />
    </div>
    <div class="form-group">
      <label for="message">Message</label>
      <textarea class="form-control" name="message" />
    </div>
    <input type="submit" value="Send" />
  </form> -->
  <div class="footer py-5">© Copyright 2021 Kip Riecken</div>
</div>

<style>
  .container-fluid {
    font-family: "Source Code Pro", monospace;
    background-color: black;
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
