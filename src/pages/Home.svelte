
<style>
    .container {
        font-family: 'Source Code Pro', monospace;
    }
    .option {
        /* flex-grow: 3; */
        /* height: 50px; */
        width: 40%;
        transition: transform 1s, border-radius 1s;
        overflow: hidden;
    }

    .option:hover {
        /* transform: scale(1.05); */
        /* border-radius: 10px; */
        transition: transform 1s, border-radius 1s;
    }

    .card-title {
    /* text-shadow: 1px 1px 2px #111; */
    justify-content: baseline;
  }
  
  .card {
    border: none;
    /* height: 22rem;
    width: 22rem; */
    margin: auto;
  }
  
  .card:hover {
    cursor: pointer;
    transform: scale(1.03);
    transition: transform 2s;
  }
  
  .card div {
    visibility: hidden;
    opacity: 0;
    transition: visibility .5s, opacity .5s;
    text-align: right;
    align-items: baseline;
  }
  
  .card:hover div {
    visibility: visible;
    background-color: rgb(0, 0, 0, 0.1);
    opacity: 1;
    transition: opacity 1s, background-color 1s;
  }
  
  .card-img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  
  .card-img:hover {
    background: rgb(0, 0, 0, 0.1);
    transform: scale(2);
    transition: transform 1s;
  }

  .sidebar-item {
    transition: transform .5s;
  }

  .sidebar-item:hover {
      color: black;
      transform: scale(1.2) translateX(-3px);
      /* background-color: darkcyan; */
      transition: transform .5s, color .5s, background-color .5s;
  }
    a span {
        color: black;
        font-size: 16px;
        background-color: white;

        position: absolute;
        top: 45%;
        right: 79%;
        margin-right: -350px;

        border-style: solid;
        border-radius: 1rem;

        transform: scale(0);
        -webkit-transform: scale(0);

        transition: opacity 1s, transform 1.5s;
        -webkit-transition: opacity 1s, transform 1.5s;
        transition-delay: 0.5s;
        -webkit-transition-delay: 0.5s;

        opacity: 0;
        z-index: 50;
    }
    a div:hover ~ span {
        opacity: 1;
        transform: scale(1);
        -webkit-transform: scale(1);
    }
</style>

<div class="container">
    <div class="row">
        <div class="col-12 col-md-2">
            <div
                class="container title text-left font-weight-heavy d-flex flex-column justify-content-center pb-5 mb-5">
                <h1 class="display-4">Kip Riecken</h1>
            </div>
        </div>
        <div class="col-12 col-md-8">
            <div class="container home card-columns">
                <div class="d-flex justify-content-center"></div>
                <div class="card bg-dark text-white option m-2" id="one">
                    <a href="https://happy-carson-6e7a3e.netlify.app/">
                        <img
                            class="card-img img-thumbnail"
                            src="images/AdventScreenS.png"
                            alt="Family outside" />
                        <div class="card-img-overlay">
                            <!-- <h5 class="card-title">Card title</h5>
                            <p class="card-text">
                                This is a wider card with supporting text below
                                as a natural lead-in to additional content. This
                                content is a little bit longer.
                            </p>
                            <p class="card-text">Last updated 3 mins ago</p> -->
                        </div>
                    </a>
                </div>
                <a href="https://happy-carson-6e7a3e.netlify.app/" class="">
                    <div><i class="fas fa-plus"></i></div>
                    <span class="p-2">
                        <div>Responsive Advent Calendar</div>
                        <!-- Put your text HERE-->
                    </span>
                </a>
                <div class="card bg-dark text-white option" id="two">
                    <a href="https://vast-garden-58006.herokuapp.com/">
                        <img
                            class="card-img img-thumbnail"
                            src="images/VotingScreenS.png"
                            alt="Family outside" />
                        <div class="card-img-overlay">
                            <h5 class="card-title"> </h5>
                            <p class="card-text">
                            </p>
                            <p class="card-text"></p>
                        </div>
                    </a>
                </div>
                <a href="https://vast-garden-58006.herokuapp.com/" class="">
                    <div><i class="fas fa-plus"></i></div>
                    <span class="p-2">
                        <div>Site for US voting information</div>
                        <!-- Put your text HERE-->
                    </span>
                </a>
                <div class="card bg-dark text-white option" id="three">
                    <a href="https://dazzling-montalcini-f8bc50.netlify.app/">
                        <img
                            class="card-img img-thumbnail"
                            src="images/meScreenS.png"
                            alt="Family outside" />
                        <div class="card-img-overlay">
                            <h5 class="card-title">Card title</h5>
                            <p class="card-text">
                                This is a wider card with supporting text below
                                as a natural lead-in to additional content. This
                                content is a little bit longer.
                            </p>
                            <p class="card-text">Last updated 3 mins ago</p>
                        </div>
                    </a>
                </div>
                <a href="https://dazzling-montalcini-f8bc50.netlify.app/" class="">
                    <div><i class="fas fa-plus"></i></div>
                    <span class="p-2">
                        <div>My personal site</div>
                        <!-- Put your text HERE-->
                    </span>
                </a>
                <div class="card bg-dark text-white option align-self-center" id="four">
                    <a href="https://wizardly-knuth-3d0e75.netlify.app/">
                        <img
                            class="card-img img-thumbnail"
                            src="images/SamScreenS.png"
                            alt="Family outside" />
                        <div class="card-img-overlay">
                            <h5 class="card-title">Sam Peterson Photography</h5>
                            <p class="card-text">
                            </p>
                        </div>
                    </a>
                </div>
                <a href="https://wizardly-knuth-3d0e75.netlify.app/" class="">
                    <div><i class="fas fa-plus"></i></div>
                    <span class="p-2">
                        <div>Photography site for a friend</div>
                        <!-- Put your text HERE-->
                    </span>
                </a>
                <!-- <img src="images/brewery.jpg"  class="option w-sm-100" id="one" alt="">
                <img src="images/Wekiva_green.jpg" class="option" id="two" alt="">
                <img src="images/KR32.jpg" class="option" id="three" alt="">
                <img src="images/disappearingmtns.jpeg" class="option" id="four" alt=""> -->
            </div>
        </div>
        <div class="col-12 col-md-2">
            <div class="container sidebar text-right">
                <ul class="list-unstyled">
                    <a href="images/TechResume.pdf">
                        <li class="sidebar-item">Resume</li>
                    </a>
                    <a href="mailto:kip.riecken@gmail.com">
                        <li class="sidebar-item">Contact</li>
                    </a>
                </ul>
            </div>
        </div>
    </div>
</div>
