# DayZ Equal Zones Tool

A single-file, browser-based tool that splits a DayZ map (or any other) image into equally sized zones for a given number of players. It runs locally in your browser.

![](/example_images/chernarus_example.png) ![](/example_images/namalsk_example.png)


## How to use
1. Try it out [here](https://lucaperl.github.io/EqualZonesTool/) or download the `index.html` and open it in a browser
2. Upload your map image.
3. Set map width (km) and players/zones.
4. If needed, enable Ocean/Ice and pick the colors on the map; adjust tolerance.
5. Click "Generate Equal Zones".
6. Hover zones for details and export as PNG.

## Tips
- If water/ice isn’t fully excluded, increase tolerance slightly.
- If land gets removed by mistake, lower tolerance.
- Higher “Calculation Precision” improves equality but takes longer.
- Very large images will take longer; resizing the map before upload can help.

## How it works (algorithm)
This uses a capacity-constrained Voronoi approach:
- Each zone has a moving center and a weight.
- Pixels are assigned to the zone whose weighted distance is smallest.
- The centers move toward the centroid of their assigned pixels.
- The weights are adjusted so each zone converges toward the same target pixel count.
- A coarse-to-fine pass is used to converge faster, then the final zones are rasterized at full resolution and borders are drawn.
