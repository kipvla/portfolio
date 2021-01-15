<script>
    import projects from "../projects";
    import Title from '../components/Title.svelte'
</script>

<style>
    .container-fluid {
        font-family: 'Source Code Pro', monospace;

    }
    /* .option {
        flex-grow: 3;
        height: 50px;
        width: 40%;
        transition: transform 1s, border-radius 1s;
        overflow: hidden;
    }

    .option:hover {
        transform: scale(1.05);
        border-radius: 10px;
        transition: transform 1s, border-radius 1s;
    } */
  
  .card {
    border: none;
    /* height: 22rem;
    width: 22rem; */
    margin: auto;
    /* transition: transform 1s; */
  }
  
  .card:hover {
    cursor: pointer;
    /* transform: scale(1.02); */
    /* transition: transform 2s; */
  }
  
  .card div {
    visibility: hidden;
    opacity: 0;
    transition: visibility .5s, opacity .5s;
    /* text-align: right; */
  }
  
  .card:hover div {
    visibility: visible;
    background-color: rgb(0, 0, 0, 0.1);
    opacity: 1;
    transition: opacity 1s, background-color 1s;
  }
  
  /* .card-img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  
  .card-img:hover {
    background: rgb(0, 0, 0, 0.1);
    transform: scale(2);
    transition: transform 1s;
  } */
/* 
  #title {
      height: 100%;
  } */

  .sidebar-item {
    transition: transform .5s;
  }

  .sidebar-item:hover {
      color: black;
      transform: scale(1.2) translateX(-3px);
      /* background-color: darkcyan; */
      transition: transform .5s, color .5s, background-color .5s;
  }

  #cards {
      align-items: flex-start;
      overflow: visible;
  }

  .sidebar {
      flex-direction: column;
      /* justify-content: flex-end; */
  }
  /* ul {
      display: inline;
  } */

  @media only screen and (max-width: 768px) {
        #all {
            flex-direction: column;
        }
        .sidebar {
            flex-direction: row;
        }
        ul {
            display: flex;
            justify-content: space-evenly;
        }
        .sidebar-item {
            margin: 0 1rem;
        }
  }
</style>

<div class="container-fluid d-flex justify-content-between" id="all">
    <Title/>
    <div class="d-flex flex-wrap justify-content-start order-1" id="cards">
        {#each projects as project}
            <div class="card" style="width: 30rem;">
                <a href="{project.url}">
                    <img class="card-img-top" src="{project.image}" alt="{project.title}">
                </a>
                <div class="card-body">
                <p class="card-text">{project.title}</p>
                </div>
            </div>
        {/each}
    </div>
    <div class="order-0 order-md-2 sidebar">
        <ul class="list-unstyled">
            <li class="sidebar-item"><a href="https://github.com/kipvla"><i class="fab fa-github"></i></a> </li>
            <li class="sidebar-item"><a href="mailto:kip.riecken@gmail.com"><i class="fas fa-envelope"></i></a> </li>
            <li class="sidebar-item"><a href="images/TechResume.pdf">resume</a> </li>
        </ul>
    </div>
</div>
