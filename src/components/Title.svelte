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
</style>

<div class="d-flex flex-column justify-content-start order-0" id="typewriter">
    kip riecken
    developer
</div>

<script>
    function setupTypewriter(t) {
        var HTML = t.innerHTML;

        t.innerHTML = "";

        var cursorPosition = 0,
            tag = "",
            writingTag = false,
            tagOpen = false,
            typeSpeed = 100,
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
    var typer = document.getElementById("typewriter");

typewriter = setupTypewriter(typer);

typewriter.type();
</script>
