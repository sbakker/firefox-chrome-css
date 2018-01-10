# firefox-chrome-css
Firefox "chrome" CSS file(s) to fix broken page elements on dark desktop (Gtk) themes.

## The Problem

When running Firefox on Linux with a dark desktop theme (e.g. Adwaita's dark theme under GNOME), various pieces of the page content suddenly don't render properly anymore. This is a combination of Firefox quirks and sloppy CSS programming. Imagine the following page content:
```
<input type="text" name="test" value="This is a test" style="color: #333333"/>
```
In default environments this would look like show an input text box with a white background (default page background) and the text "This is a test" in a dark grey font.

Now, it seems that Firefox picks up its default page colours from the user's desktop theme. For light colours that's not a problem (see above), but when selecting a dark desktop theme, e.g with a background colour of `#333333` and a foreground colour of `#eeeeee`, Firefox will now use those colours as its default page colours. This has the nice effect that pages without any special styling will automatically get the dark theme applied. Unfortunately, for pages that don't specify both foreground and background colour for an element, the effect is horrible. Take the example above: the `<input>` element inherits the background colour from its parents, which will default to the browser default (`#333333`); the text colour is explicitly set to `#333333`, so we will now effectively have invisible text. 

## The "Solution"

Firefox allows the user to override browser defaults with `userChrome.css` and `userContent.css`. The former deals with browser UI elements, the latter with page content.

This repository focuses mainly on the page content. It attempts to create page styles that make most sites workable, if not pretty.

## Installation

Clone this repository to the `chrome` sub directory of your default Firefox profile, e.g.:

```
cd ~/.mozilla/firefox/*.default
git clone https://github.com/sbakker/firefox-chrome-css.git chrome
```

Next, restart Firefox.
