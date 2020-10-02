# manipulation-data
Media and data files associated with the manipulation textbook (in the manipulation repo)

Note: with two-factor authentication, I need to use the token instead of the password to push to https from the command line.


## matplotlib animations

I've been adding a little javascript 
```
    function getParameterByName(name) {
    name = name.replace(/[\[]/, "\\[").replace(/[\]]/, "\\]");
    var regex = new RegExp("[\\?&]" + name + "=([^&#]*)"),
      results = regex.exec(location.search);
    return results == null ? "" : decodeURIComponent(results[1].replace(/\+/g, " "));
    }
    var height=getParameterByName("height")
    if (height) {
      document.getElementById(img_id).style.height = height;
    }    
```
just after the line starting with `var img_id =` so that I can control the size from the iframe.  Then I pass `?height=240px` into the iframe url.

## SVGs

To resize the SVGs I got out of matplotlib, I opened them in Inkscape, ungrouped the main group.  Selected the important objects, and did Edit>Resize Page to Selection.  Then saved.

I've also made a few figures in slides.com by exporting the presentation to pdf, cropping in acrobat, then converting to SVG with pdf2svg.

## Meshcat animations

To make meshcat animations save to html, the workflow (at least with MeshcatVisualizer) is roughly:

```
meshcat.vis['/Background'].set_property("visible", False)
meshcat.start_recording()
simulator.AdvanceTo(args.duration)
meshcat.stop_recording()
meshcat.publish_recording(repetitions=np.inf)
f = open("animation.html", "w")
f.write(meshcat.vis.static_html())
f.close()
```

## Colab

When I generate files on colab, i can download them with
```
from google.colab import files
files.download("animation.html")
```