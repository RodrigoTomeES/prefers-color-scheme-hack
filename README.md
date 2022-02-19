# Prefers Color Scheme Hack 🌗

<div align="center">
    <img src="header.svg" alt="Header of prefers color scheme hack">
</div>

<br>

The `prefers-color-scheme` is a CSS media feature, it is used to detect if the user has requested a light or dark color theme. This feature only can be used in `<style>` tag or in `js` but Github doesn't allow it in READMEs because you could easily launch a phishing attack.

For this reason I searched for a workaround and I found an article of [Chris Coyier in CSS Tricks](https://css-tricks.com/custom-styles-in-github-readmes/) that talk about add custom CSS in a SVG file. With this idea in mind I supposed that it would be possible to use the `prefers-color-scheme` media feature with this feature, and it worked! 🚀

## Example

I think the best way to see it is with an example, so let's go:

```xml
<svg width="200" height="200" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
	<foreignObject width="100%" height="100%">
		<div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; height: 100%;">
            <style>
                .example {
                    width: 250px;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    background: #EEEEEE;
                    color: black;
                    font-family: sans-serif;
                    font-size: 25px;
                    text-align: center;
                }

                .example::after {
                    content: 'You are using a light theme';
                }

                @media (prefers-color-scheme: dark) {
                    .example {
                        background: #323232;
                        color: white;
                    }

                    .example::after {
                        content: 'Welcome to the dark side';
                    }
                }
            </style>
            <div class="example"></div>
		</div>
	</foreignObject>
</svg>
```

### Result

<div align="center">
    <img src="example.svg" alt="Example of use prefers color scheme">
</div>

## Advanced use

This tecnic for use `prefers color scheme` can be use in proyect like [github-readme-activity-graph](https://github.com/Ashutosh00710/github-readme-activity-graph) and you can get a stat image that can change with your them browser preferences. In the case of the `github-readme-activity-graph` project, I have made an example implementation that you can find [here](https://github.com/RodrigoTomeES/github-readme-activity-graph).

### Example

<img src="https://stormy-sea-99716.herokuapp.com/graph?username=rodrigotomees&bg_color=0d111700&color=FFFFFF&line=1f6feb&point=FFFFFF&hide_border=true&pcs_light[bg_color]=0d111700&pcs_light[color]=24292F&pcs_light[line]=1f6feb&pcs_light[point]=24292F" alt="Example of advanced use">

## Limitations

Using prefers color scheme doesn't work in Github apps (android / ios) because always return the light theme. I don't know if this is a bug of the app or it isn't compatible with this feature.

## Resources Used

- [Custom Styles in GitHub Readme Files article by Chris Coyier](https://css-tricks.com/custom-styles-in-github-readmes/)
- [Example website of dark mode by phre1](https://github.com/ditdot-dev/dark-mode-example)
