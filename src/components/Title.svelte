<script>
  import { onMount } from "svelte";
  import { scale } from "svelte/transition";

  export let color;

  onMount(() => {
    var typer = document.getElementById("typewriter");
    function setupTypewriter(t) {
      var HTML = t.innerHTML;

      t.innerHTML = "";

      var cursorPosition = 0,
        tag = "",
        writingTag = false,
        tagOpen = false,
        typeSpeed = 400,
        tempTypeSpeed = 0;

      var type = function () {
        if (writingTag === true) {
          tag += HTML[cursorPosition];
        }

        if (!writingTag && tagOpen) {
          tag.innerHTML += HTML[cursorPosition];
        }
        if (!writingTag && !tagOpen) {
          if (HTML[cursorPosition] === " ") {
            tempTypeSpeed = 0;
          } else {
            tempTypeSpeed = Math.random() * typeSpeed + 50;
          }
          t.innerHTML += HTML[cursorPosition];
        }

        cursorPosition += 1;
        if (cursorPosition < HTML.length - 1) {
          setTimeout(type, tempTypeSpeed);
        }
      };

      return {
        type: type,
      };
    }
    let typewriter = setupTypewriter(typer);
    setTimeout(() => {
      typewriter.type();
    }, 1000);
  });
</script>

<div class="d-flex flex-column justify-content-start order-0">
  <h1
    transition:scale={{ duration: 5000, opacity: 0.5, start: 0.5 }}
    style="color: {color}"
    class="my-2"
  >
    kip riecken
  </h1>
  <span id="typewriter" style="color: {color}">developerr</span>
  <div class="my-4">
    <a href="https://github.com/kipvla" class="text-dark btn rounded-circle"
      ><i class="fab fa-github" style="color: {color}" /></a
    >
    <a href="https://codepen.io/krvla" class="text-dark btn rounded-circle"
      ><i class="fab fa-codepen" style="color: {color}" /></a
    >
    <a
      href="https://www.linkedin.com/in/kipriecken/"
      class="text-dark btn rounded-circle"
      ><i class="fab fa-linkedin-in" style="color: {color}" /></a
    >
    <a href="mailto:kip.riecken@gmail.com" class="text-dark btn rounded-circle"
      ><i class="fas fa-envelope" style="color: {color}" /></a
    >
    <a
      href="images/Tech Resume.pdf"
      class="ml-2 text-dark"
      style="color: {color}!important">resume</a
    >
  </div>
</div>

<style type="text/scss">
  #typewriter {
    font-size: 2em;
    margin: 0;
    font-family: "Courier New";
  }

  #typewriter:after {
    content: "|";
    animation: blink 500ms linear infinite alternate;
  }

  div > a:hover {
    background: pink;
    transition: all 500ms;
  }

  @-webkit-keyframes blink {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

  @-moz-keyframes blink {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

  @keyframes blink {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
  div {
    text-align: left;
  }
  h1 {
    font-size: 3rem;
  }

  @media only screen and (max-width: 768px) {
    div {
      align-self: flex-start;
    }
  }
</style>
