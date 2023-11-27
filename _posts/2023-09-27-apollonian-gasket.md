---
layout: post
title: Tinkering around with the Apollonian Gasket
subtitle: Fractals are the covergirl of mathematics
cover-img: /assets/img/apollonian/cover.png
thumbnail-img: /assets/img/apollonian/thumb.jpg
tags: [math]
---

# How it started

I was browsing Twitter (or X to be trendy...now that Twitter = X, we might as well rebrand "tweet". My vote would be for "zap") and came across this tweet:

<div style="display: flex; justify-content: center; text-align: center;">
 <div class="image">
    <img src="/assets/img/apollonian/tweet.png" width="500"/>
    <p>Oho, this looks cool</p>
</div>
</div>

Like seeing an image of a salamandar for the first time, I decided I just had to know more. I thought it might be a quick and interesting mini project to try to generate them, and thought it would be nice to extend this to a three dimensional sphere fractal generation. But "quick" left the picture after I started to realize the complexities and rabbit holes in generating these fractals. This post is about some of the things I learned when trying to generate these fractals, setbacks, and the general process that I took. 


# Process
In order to generate the spherical fractal, I wanted to start with the "easy" case: generating a classic 2D apollonian gasket. An Apollonian gasket is a type of fractal and I think the best definition is how it is generated:

1. Start with three mutually tangent circles (each circle is tangent to the others)
2. Add an "inner" circle tangent to the previous three and "outer" circle (also tangent to the previous three). Now the base of the fractal is complete.
3. In each triangular looking whitespace, draw a new circle tangent to the three bordering circles.
4. Repeat step three with the newly created circles and respective whitespaces.

I started from the very beginning (a very good place to start) and worked on generating the initial three circles. There's two primary things that define a circle: it's centroid and radius. My initial approach was to generate a random circle, and then find another circle that was tangent to the original, and then find a third. As I started with this approach, I found it becoming messy. I had to find either a second random centroid or radius (turns out a random centroid was a lot easier), and then find a third centroid and radius that intersected with the first two at exactly one point. The first step was turning out to be hard with this approach, and after seeing this image [http://www.malinc.se/math/geometry/apolloniangasketen.php]. I realized that it would be much easier to start with three random centroids, and then find the radii which would make the circles mutually tangent. 

Because some things are easier done on paper, here is how I solved the for the radii given centroids.

<div style="display: flex; justify-content: center; text-align: center;">
 <div class="image">
    <img src="/assets/img/apollonian/Circle.png" width="500"/>
    <p>Solving for radii of circles given centroids</p>
</div>
</div>

But, this aproach had an oversight -- nested circles. I was currently ignoring all cases where one circle was inside of the other. My solution would not be able to account for something like this.


<div style="display: flex; justify-content: center; text-align: center;">
 <div class="image">
    <img src="/assets/img/apollonian/Circle1.png" width="500"/>
    <p>Impossible case</p>
</div>
</div>

Different combinations of radii have to be considered in order to fix this problem. Here's an illustration of the new cases added. 

<div style="display: flex; justify-content: center; text-align: center;">
 <div class="image">
    <img src="/assets/img/apollonian/Newcircle.png" width="500"/>
    <p>Solving for all radii of circles given centroids</p>
</div>
</div>

There are $3^3=27$ different combinations of matrices to solve, but many do not have valid solutions. I wrote a small python script to go through all 27 cases and determine the solution (if one existed).  

<div style="display: flex; justify-content: center; text-align: center;">
 <div class="image">
    <img src="/assets/img/apollonian/all_combinations.png" width="500"/>
    <p>Radii combinations</p>
</div>
</div>

Now, it was time to turn to the problem of generating the Soddy circles, or the inner and outer circles that are both tangent to the original three. My initial approach here I'm a bit emberassed to write was to consult the internet and ChatGPT. ChatGPT suggested a couple of times to use the weighted average of the centroids and radii that seemed somewhat intuitive, but when implemented, it was clear that the newly generated circles were not tangent to the original three. 

Before turning to the code, I solicited help with trying to construct all five base circles (the three original tangent circles, plus the inner and outer Soddy circle) with just a compass and ruler. We were able to construct the first three tangent circles, and thought we had a solution for the inner Soddy circle, which was to take the centroid of the triangle whose vertices were the points of tangency to the original three. I'm not sure if this is a valid solution, but on the circles we drew on paper, it seemed to work. After trying to construct the circles for a while, my co-investigtor suggested to use Solidworks and verify the construction. It took about 5 minutes using Solidworks to create the five base circles! It was a good reminder that using modern tools can be very helpful.

Coding geometry is not something I'm familiar with, and while I found geometric ways to construct the inner and outer Soddy circles online, translating this to something in code posed a challenge. A friend recommended to me to look up the method of intersecting hyperbolas and consult [this Wikipedia page](https://en.wikipedia.org/wiki/Problem_of_Apollonius), which ended up being incredibly informative. The method of intersecting hyperbolas is rather beautiful, and although I think the Wikipedia article does a great job explaining it, here's an illustration of how I came to understand it a bit better.


<div style="display: flex; justify-content: center; text-align: center;">
<div class="image">
    <img src="/assets/img/apollonian/Hyperbolas.png" width="500"/>
    <p>Intersecting hyperbolas</p>
</div>
</div>

The thing I love about the method of intersecting hyperbolas is that it leverages the definion of a hyperbola, which is simply the set of points such that the difference of the distances from two fixed points is the same. I ran into trouble trying to implement this solution in code. Upon reflection, it probably would have been a good idea to use a software like Solidworks or GeoGebra or even Desmos as a base to encode the geometric solutions. Instead, I kept searching for papers and found a [paper](https://forumgeom.fau.edu/FG2007volume7/FG200726.pdf) that detailed the derivation of an equation that could be used to find the inner and outer Soddy centroids and radii. It's an interesting read into Descarte's theorem and how to find the centroids. When I added these circles to the script, I found some strange behavior. Below are the results

<div style="display: flex; justify-content: center; text-align: center;">
    <div class="image" style="display: inline-block; margin-right: 20px;">
        <img src="/assets/img/apollonian/soddy_trial1.png" width="500"/>
        <p>Soddy circles appear in unexpected positions</p>
    </div>
    <div class="image" style="display: inline-block;">
        <img src="/assets/img/apollonian/soddy_trial2.png" width="500"/>
        <p>Expected Soddy circle placement</p>
    </div>
</div>

Above, while the soddy circles are sometimes correctly placed if the three base circles are all externaly tangent, they are never correctly placed in the other cases. In the interally tangent circle cases (green, red, and yelllow graphs), consider finding a circle with a larger radius than the given circles. Then, this must be tangent to the greatest circle and the other two circles. However, this is impossible due to the fact that the point of tangency does not coincide with the existing internal circles. In a case where the centroids all are along the same line, a circle could exist, but this is somewhat of a degenerate case. 

At this point, I admit I was getting a bit tired of the problem, and wanted a fast track solution to code up something that at least looked cool. In order to generate a fractal recursivly of tangent circles, I decided to focus on the case of the three externally tangent circles and let the mystery of the outer Soddy circle remain unsolved. I decided to use javascript to generate the fractal because of the nice THREE.js library. I find myself using Python for so many personal projects that it was also nice to get my hands a bit dirty with a different language.

The last major step was to generate the recursive circles. I opted to fist find the radius of the new tangent circles using Descarte's theorem and then a system of equations and solve for the centroid of the new tangent circles. I went off script (literally) from an Apollonian gasket and ended up generating fractal circles that were tangent to each other, but not quite Apollonian, since not all triangular whitespaces ended up being filled in. However, it looked pretty enough, and I was satisfied with the results. I also ended up generating spheres in three dimensions, based on the coordinates of an equilateral tetrahedron. Adding randomness in 3D became complicated quickly, and so I stuck to the basics here.

<div style="display: flex; justify-content: center; text-align: center; flex-wrap: wrap;">
    <div class="image" style="display: inline-block; margin: 10px;">
        <img src="/assets/img/apollonian/apollonian.png" width="400"/>
        <p>Fractal with circles colored by stage generation</p>
    </div>
    <div class="image" style="display: inline-block; margin: 10px;">
        <img src="/assets/img/apollonian/6stagesradius.png" width="400"/>
        <p>6 stage generation colored by radius</p>
    </div>
    <div class="image" style="display: inline-block; margin: 10px;">
        <img src="/assets/img/apollonian/6stages.png" width=600"/>
        <p>6 stage colored by generation</p>
    </div>
    <div class="image" style="display: inline-block; margin: 10px;">
        <img src="/assets/img/apollonian/3d.png" width="400"/>
        <p>Spheres based on equilateral tetrahedron</p>
    </div> 
</div>


Here is the [link to my Github repository](https://github.com/Aloha-Churchill/apollian-spheres) for this project. Feel free to check it out and play around with it.

# Conclusions
* I am slowly adjusting my estimation of time that projects take. Unforseeable bugs catch me up often. As an example, constructing a circle in THREE.js is simple, but I wanted a circle without contours (which appear by default), and this took time to figure out even though it was somewhat irrelevatnt to the problem at hand. I ended up actually generating the circles by calulating points along the circumference and connecting them with lines.
* Even though this project is arguably not completed, it is time I think to put it to rest. I sometimes wonder when looking at paintings when the artist knows she or he is done. It seems that there could always be more touch ups, but with that approach, you wouldn't get to paint many pieces! 
* It's so easy for me to get in the habit of turning to quick solutions or asking ChatGPT. I found it a very nice practice to have just a compass and ruler and try to figure things out without the internet.

