# muggin
<h3>An HTML template language that piggybacks off of Pug JS, but with a curly-brace syntax for (in my opinion) better readability.</h3>

To install:
```npm install [repo directory] -g```

To use:
```muggin [input.mug] [anotherfile.mug]```
  this generates index.html and anotherfile.html
	
  
<b>Example syntax:</b>

```

doctype html

// Indentation is still enforced
html(lang="en") {
    head {
        meta(charset="utf-8")
        title Title!

        // "~>" denotes begining of style or script
        style ~> {
            body {
                background-color: #212121;
            }
            .yellow {
                color: #ffff00;
            }
        }

        script(src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js")
        script(type="text/javascript") ~> {
            async function fetchState() {
                let response = await fetch("https://api.kanye.rest/")
                let json = await response.json()
                return json
            }

            $(document).ready(() => {
                fetchState().then(state => {
                    $("#quote").text(state.quote)
                })
            })
        }
    }

    body {
        #main {
            h1.yellow Header!
            p.yellow Paragraph!
            #quote.yellow
        }
    }
}

```
