# manipulation-data
Media and data files associated with the manipulation textbook (in the manipulation repo)

## SVGs

To resize the SVGs I got out of matplotlib, I opened them in Inkscape, ungrouped the main group.  Selected the important objects, and did Edit>Resize Page to Selection.  Then saved.


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