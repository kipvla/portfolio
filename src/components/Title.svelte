<script>
    import { onMount } from "svelte";
    
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
        typewriter.type();
    });
</script>

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
            padding-left: 1rem;
        }
    }
</style>

<div class="d-flex flex-column justify-content-start order-0">
    <h1>kip riecken </h1><span id="typewriter">developerr</span>
</div>
