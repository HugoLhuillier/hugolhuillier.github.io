---
layout: post
title: untitled 1
description:
img: /ext-files/imgs/visualization/untitled1.png
---

<div class="img_row">
	<img src="{{ site.baseurl }}/ext-files/imgs/visualization/untitled1.png" width="780"  title="contour plot"/>
</div>

Here is the associated code.

```julia
using PyPlot
x   = linspace(-3pi, 3pi, 100)
y   = linspace(-3pi, 3pi, 100)
z1  = [[cos(xi) * tan(yj) for yj in y] for xi in x]
z2  = [[cos(xi) * cos(yj) for yj in y] for xi in x]
x   = repmat(x, 1, 100)
y   = repmat(y', 100, 1)

fig = figure("", figsize = (10, 10))
ax  = fig[:add_subplot](1, 1, 1)
# remove the ticks and labels on the axes
ax[:xaxis][:set_tick_params](which = "both", bottom = "off", top = "off", labelbottom = "off")
ax[:yaxis][:set_tick_params](which = "both", bottom = "off", top = "off", labelbottom = "off")

limits = [[-0.4, 0.4], [-0.5, 0.5], [-0.6, 0.6], [-0.95, 0.95]]
col    = ["darkorange", "orange", "navajowhite", "red"]
for i in 1:length(limits)
  ax[:contour](x, y, z1, limits[i], linewidth = 1, colors = col[i])
  ax[:contour](x, y, z2, limits[i], linewidth = 1, colors = col[i])
end
```
