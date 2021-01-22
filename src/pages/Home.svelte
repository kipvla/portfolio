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
        margin: auto;
        transition: transform 0.2s;
    }

    .card:active {
        transform: scale(0.96);
        transition: transform 0.2s;
    }

    .card:hover {
        cursor: pointer;
    }

    .card div {
        visibility: hidden;
        opacity: 0;
        transition: visibility 0.5s, opacity 1s;
    }

    .card:hover div {
        visibility: visible;
        background-color: rgb(0, 0, 0, 0.5);
        opacity: 1;
        transition: opacity 1s, background-color 1s;
    }

    #cards {
        align-items: flex-start;
        overflow: visible;
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
    <div class="footer">
        © Copyright 2021 Kip Riecken
    </div>
</div>
