# firefox-chrome-css
Firefox "chrome" CSS file(s) to fix broken page elements on dark desktop (Gtk) themes.

## The Problem

When running Firefox on Linux with a dark desktop theme (e.g. Adwaita's dark theme under GNOME), various pieces of the page content suddenly don't render properly anymore. This is a combination of Firefox quirks and sloppy CSS programming. Imagine the following page content:
```
<input type="text" name="test" value="This is a test" style="color: #333333"/>
```
In default environments this would look like:

<span style="color: #333333; background-color: #ffffff; border:1px solid #888888;"/>This is a test</span>


Firefox allows the user to override browser defaults with `userChrome.css` and `userContent.css`. The former deals with browser UI elements, the latter with page content.
