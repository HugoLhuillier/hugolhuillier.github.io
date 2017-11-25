---
layout: post
title: Lavoir
description:
img: /ext-files/imgs/visualization/lavoir.png
---

<div class="img_row">
	<img src="{{ site.baseurl }}/ext-files/imgs/visualization/lavoir.png" width="780"  title="lavoir"/>
</div>

Here is the associated code.

```julia
# create the data
X    	= linspace(-10, 10, 50)
Y   	= linspace(-10, 10, 50)
z1  	= [[x * cos(y) * cos(x * y) + y * cos(x) * cos(x * y) + x * y * cos(x) * cos(y) for y in Y] for x in X]
z2   	= [[rand(1)[1] * cos(x * y) * sin(y)^2 + rand(1)[1] for y in Y] for x in X]
z3   	= [[(rand(1)[1] * 0.2 + 0.8) * (x^2 + y^2) for y in Y] for x in X]
X   	= repmat(X, 1, 50)
Y   	= repmat(Y', 50, 1)

# create the figure
fig 	= figure("", figsize = (10, 10))
ax  	= fig[:add_subplot](1, 1, 1)
# remove the ticks
ax[:xaxis][:set_tick_params](which = "both", bottom = "off", top = "off", labelbottom = "off")
ax[:yaxis][:set_tick_params](which = "both", bottom = "off", top = "off", labelbottom = "off")
# plot the data
ax[:contourf](X, Y, z2, cmap = "Blues")
ax[:contourf](X, Y, z1, [-Inf, -12.0], colors = "mediumseagreen")
ax[:contourf](X, Y, z1, [-Inf, -80.0], colors = "white")
ax[:contourf](X, Y, z1, [-60, -50.0], colors = "white")
ax[:contourf](X, Y, z1, [-80, -57.0], colors = "yellow")
ax[:contour](X, Y, z1, [-15.0], colors = "g", linestyles = "solid")
ax[:contour](X, Y, z3, [2.0, 3.0, 4.0, 6.0, 8.0, 14.0, 20.0], colors = "steelblue", alpha = 0.4)
ax[:scatter]([0.0],[0.0],color="black",alpha=0.5)
```
