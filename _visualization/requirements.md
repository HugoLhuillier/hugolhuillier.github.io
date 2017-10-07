---
layout: post
title: requirements
description:
img: /ext-files/imgs/requirements.gif
---

Here is a list of stuff you need on your computer if you want to follow the "tutorials" and reproduce the animations

1. `Julia`, a top notch open source programming language, that you can download [here](https://julialang.org/) for free
1. The `PyPlot.jl` package

and that's it! The [first post](/visualization/2D_system) explains in detail how to produce animations and gifs with `PyPlot.jl`.

`PyPlot.jl` is a bit more difficult to manage than other plotting packages, and the best documentation available is unfortunately the [Python documentation](https://matplotlib.org/). But it is also more flexible than packages like `Plots.jl`, which is crucial for what we want to do here.

And you can still [create cool plots](https://gist.github.com/gizmaa/7214002) in about 10 lines of code, like this one.

<div class="img_row">
	<img src="{{ site.baseurl }}/ext-files/imgs/visualization/demo_pyplot.png" width="580"  title="contour plot"/>
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
