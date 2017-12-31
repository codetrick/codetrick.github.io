---
layout: post
title:  "Polygon Turning Explained"
date:   2017-12-31 13:10:52 -0800
published: true
categories: hardware
---

I came across [this video](https://www.youtube.com/watch?v=ATgT1nt02PY) on YouTube a couple days back. As a novice machinist I was initially very confused - aren't lathes supposed to be used to turn parts into axial-symmetric shapes? How is it possible to make, say a hexagon, with an engine lathe?

Ok, I get that you'll need two spindles (part spindle, and live tooling spindle) that somehow are synchronized together, but how exactly can you produce a flat surface, given that both the part and the cutter are spinning, tracing out curves instead of straight lines?

<!--more-->

I checked Wikipedia, and found a [page](https://en.wikipedia.org/wiki/Polygonal_turning) on this subject. However it isn't very well written and doesn't actually explain how it really works.

To figure out what is really going on in polygon turning, it's best to visualize the path traced out by the tips of the cutters. But the part being cut is also rotating, you say. Then let's work in a non-inertial frame co-rotating with the part spindle. In this reference frame the part is stationary, but the motion of the cutters is slightly more complicated. The center of the cutter wheel is rotating around the center of the part with angular speed $$\Omega$$, while the cutter wheel itself is rotating with angular speed $$\omega$$. The tips of the cutters would trace out a curve much like [epitrochoids](https://en.wikipedia.org/wiki/Epitrochoid), but not quite. Unlike epitrochoids, here the direction of the two rotations are opposite, $$\Omega \cdot \omega < 0$$.

With Mathematica it's easy to visualize the curve. First, some explanation of tunable parameters is due. Let's set the cutting edge diameter to be 1, and denote by $$R$$ the distance between the center of the part and the center of the cutter wheel. Then I will call the ratio of the two angular speed $$k = - \omega / \Omega$$ the revolution ratio. The number of (evenly spaced) cutters on the cutter wheel is denoted by $$l$$.

The first example would be for turning a hexagon. See the code and plot below.

![hexagon cutter trace]({{ site.url }}/assets/2017/12/hexagon_one_cutter.png)

The blue circle marks the trace of the center of the cutter wheel, while the orange curve marks the path of the cutter tip. Note that the curve is everywhere convex. But the part closest to the origin looks almost flat. Now if we put three cutters around the cutter wheel, then the traces would be 120 and 240 degrees rotated, resulting in the curve shown below:

![full hexagon]({{ site.url }}/assets/2017/12/hexagon_full.png)

The three cutters indeed give you an approximated hexagon! Polygon turning is as simple as this! You can even do pentagons!

![full pentagon]({{ site.url }}/assets/2017/12/pentagon_full.png)

But how do you determine what revolution ratio $$k$$ and number of cutters $$l$$ for a given polygon? A good rule of thumb is have the number of faces $$n = k \cdot l$$. You still have the freedom to pick the integer $$l$$. Say you want to turn a triangle, then you can either have $$l=3, k=1$$, or $$l=2, k=1.5$$, or $$l=1, k=3$$. These different choices will result in different shapes of the "flat" face. A large $$l$$ will give you a convex face, while a small $$l$$ will result in a concave face. On page J23 of [this catalog][horn catalog] from Horn USA, general advice on what revolution ratio and number of inserts to be used can be found. Of course, you can calculate the exact resulting shape in Mathematica as I have just shown!

Please let me know if anything is unclear in my article, and thanks for reading!

[horn catalog]: http://www.hornusa.com/fileadmin/user_upload/usa/PDF/HORN-US-Chapters/KFRAES100US_3.2013/KFRAES100US_3.2013_ChapterJ_Polygon-Milling.pdf
