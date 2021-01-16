<script>
    import projects from "../projects";
    import Title from "../components/Title.svelte";
</script>

<style>
    .container-fluid {
        font-family: "Source Code Pro", monospace;
    }

    .card {
        border: none;
        /* height: 22rem;
    width: 22rem; */
        margin: auto;
        /* transition: transform 1s; */
    }

    .card:active {
        transform: scale(0.96);
    }

    .card:hover {
        cursor: pointer;
        /* transform: scale(1.02); */
        /* transition: transform 2s; */
    }

    .card div {
        visibility: hidden;
        opacity: 0;
        transition: visibility 0.5s, opacity 0.5s;
        /* text-align: right; */
    }

    .card:hover div {
        visibility: visible;
        background-color: rgb(0, 0, 0, 0.5);
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
        transition: transform 0.5s;
    }

    .sidebar-item:hover {
        color: black;
        transform: scale(1.2);
        /* background-color: darkcyan; */
        transition: transform 0.5s, color 0.5s, background-color 0.5s;
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
        #sidebar {
            display: flex;
            justify-content: space-evenly;
        }
        .sidebar-item {
            margin: 0 1rem;
        }
    }
</style>

<div class="container-fluid justify-content-between" id="all">
    <Title />
    <br />
    <div class="d-flex flex-wrap justify-content-start order-1" id="cards">
        {#each projects as project}
            <div class="card my-4 shadow-lg" style="width: 30rem;">
                <a href={project.url}>
                    <img
                        class="card-img-top"
                        src={project.image}
                        alt={project.title} />
                    <div
                        class="card-img-overlay d-flex flex-column justify-content-end">
                        <p class="card-text text-white" />
                        <ul class="list-unstyled">
                            {#each project.specs as spec}
                                <li class="text-left text-white">{spec}</li>
                            {/each}
                        </ul>
                    </div>
                </a>
                <!-- <div class="card-body">
                    <p class="card-text">{project.title}</p>
                </div> -->
            </div>
        {/each}
    </div>
    <div class="order-0 order-md-2 sidebar">
        <ul class="list-unstyled" id="sidebar">
            <li class="sidebar-item">
                <a href="https://github.com/kipvla"><i
                        class="fab fa-github" /></a>
            </li>
            <li class="sidebar-item">
                <a href="mailto:kip.riecken@gmail.com"><i
                        class="fas fa-envelope" /></a>
            </li>
            <li class="sidebar-item">
                <a href="images/TechResume.pdf">resume</a>
            </li>
        </ul>
    </div>
</div>
