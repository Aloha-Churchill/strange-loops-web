---
layout: post
title: The Mobius strip of life
subtitle: A beginning of an end and an end of a beginning 
cover-img: /assets/img/BLOG_COVERS/8.jpeg
thumbnail-img: /assets/img/BLOG_THUMBNAILS/0_rosette.jpg
tags: [math]
---

### ```intro: ```

When I was first learning how to write a 5 paragraph analysis essay, we were told that the conclusion should mirror the introductory paragraph. At the time, I found this a bit silly and would often (especially when the assignment was due the day I began with it) wind up copying and pasting the introduction straight to the end and rephrase a bit. This was in the age before advanced large language models, and bogglingly (what a great word, although using it feels like committing grammar treason to use it) rephrasing was done manually. My approach and attitute towards the conclusion was entirely wrong. The process of *discovering a conclusion*, whether it connects to introduction or not is the essence of learning. This is the primary reason why the Strange Loops platform was created: to explore and share ideas and projects. In some explorations, the concluding thoughts or project completion might match closely with the initial approach; in others the end might spiral off away and away from the beginning. Either way, my hope is that sharing at least a bit of the process might be helpful or intriguing, or at least could help me better arrange my thoughts. I like the idea of learning in public, recieving feedback or corrections since there's sure to be mistakes or misconceptions in my understanding or approaches, and contributing to the open source trove of information. In this first post, I'd like to learn a bit more about what "strange loops" are and get a feel for what it's like to write a blog post.
# Strange Loops
The first time I encountered a strange loop came with a twist -- literally. The Mobius strip is a tricky little topographic shape. It's a single sided surface that is not orientable. If you imagine an ant (or any animal you desire, ants have just somehow become linked to exploring manifolds) doing a complete loop by traversing along the surface, when it gets back to where it started, the ant's left and right will have flipped. It took some time to wrap (pun intended and relished) my head around this. After leaving little Mobius strips all over the place, I didn't think about them for years. But a couple months ago, I was reading the first few pages of "Godel, Escher, and Bach" and Mobius strips were mentioned in the context of "strange loops". I think the best "strange loop" definition that I've seen comes from Hofstater, the auther of "Godel, Escher, and Bach" (and incidentally, also the author of "I Am a Strange Loop" -- no wonder he really understands these :)). 

> "What I mean by "strange loop" is — here goes a first stab, anyway — not a physical circuit but an abstract loop in which, in the series of stages that constitute the cycling-around, there is a shift from one level of abstraction (or structure) to another, which feels like an upwards movement in an hierarchy, and yet somehow the successive "upward" shifts turn out to give rise to a closed cycle. That is, despite one's sense of departing ever further from one's origin, one winds up, to one's shock, exactly where one had started out. In short, a strange loop is a paradoxical level-crossing feedback loop. (pp. 101-102 in "I Am a Strange Loop")" **~ Douglas Hofstadter**

Strange loops are a fascinating idea and can delightfully, yet unexpectedly, be found all over the place, like easter eggs in winter. Below are some examples. Note the topics with astrisks are ones I made up when thinking about strange loops and should be taken with a grain (or maybe even a good teasopoon) of salt. 

## Natural Language
#### This statement is false. 
The quintessential strange loop of natural language. Think about it too hard and soon you may be experiencing a sensation similar to getting off of one of those twirly park structures.

#### All generalizations are false, including this one. ~ Mark Twain

#### The future ain't what it used to be. ~ Yogi Berra
A lot of [Yogi Berra's quotes](https://ftw.usatoday.com/2019/03/the-50-greatest-yogi-berra-quotes) are self-referential, interesting, and amusing.

#### I can't think while I'm metacognating.*

Pro tip: don't use this phrase in any social situation. 

#### Thesaurus and Dictionaries*
My initial thought here is that language, even though it evolves, is a closed system. To get a true meaning of a word, each word in its definition needs to be defined and so on. If you were to represent each word as a node in the graph, and add an edge to a word in it's definition, loops would exist in this graph. The question then has to be asked if this should be categorized as a loop or a *strange* loop. Because progress seems like its being made in one direction but then winds up at the beginning, I put this under the strange loop category.
## Programming

#### Quines
A quine is a program that prints out its own source code. 

```
exec(s:='print("exec(s:=%r)"%s)')
```

1. ```s``` is assigned to the ```print``` statement
2. ```%r``` in the format string is a string representation of the object that is passed to it, in this case the string representation of s
3. ```exec()``` function executes the print function
4. ```print()``` uses formatted printing to replicate the source code

While the process of executing a program goes from source code to result, in this case, the end result is the source code. It's hard to concieve of a practical use of quines, but c'est la vie.  If quines sound interesting, then checko out [this video](https://www.youtube.com/watch?v=6avJHaC3C2U).

And [this video](https://www.youtube.com/watch?v=ar9WRwCiSr0) was the reason I put quines under the strange loop category. 

#### Overflow*
In coding, a traditional loop is a powerful thing and can make repetivite, computationally intensive tasks (something that compters are very good at) quick and simple. For example, here's a construction of the set of positive integers in just a few lines.  

```
always_stay_positive = set()
i = 1
while (1):
    always_stay_positive.add(i)
    i ++ 
```

And off ```i``` sails, going up and up and, you guessed it, up. But a curious thing can happen when a number tries to become *too* large. Just as the number is getting promoted -- kaboom -- all of a sudden, that large number crashes down, becoming tiny again. This is called "overflow". Here's a nice illustration of unsigned integer overflow.

<div style="display: flex; justify-content: center; text-align: center;">
 <div class="image">
    <img src="/assets/img/strangeloops/UnsignedWheel.png" width="500"/>
    <p>Unsigned integer overflow</p>
</div>
</div>

Here, a loop which was supposed to construct a monotonically increasing sequence, became a different type of loop and perhaps could even be considered a strange loop. Related to the idea of overflow is the modulus operator. The modulus operator is not, of course, a loop itself, but applying it to a sequence can result in this same cyclic behavior that happens with overflow. 
## Art
#### M.C. Escher Artwork

<div style="display: flex; justify-content: center; text-align: center;">
    <div class="image" style="display: inline-block; margin-right: 20px;">
        <img src="/assets/img/strangeloops/artworks-000484723125-lxkye9-t500x500.jpg" width="500"/>
        <p>Ascending and Descending</p>
    </div>
    <div class="image" style="display: inline-block;">
        <img src="/assets/img/strangeloops/download.jpg" width="500"/>
        <p>Relativity</p>
    </div>
</div>

#### Waterfall

<div style="display: flex; justify-content: center; text-align: center;">
 <div class="image">
    <img src="/assets/img/strangeloops/waterfall.gif" width="500"/>
    <p>Or perhaps a water-rise?</p>
</div>
</div>


## Math
#### Russell's Paradox and the Foundation of Math

Because sometimes rephrasing a great explination is as fruitless as thoroughly washing dishes before putting them in the dishwasher, here's a [great explination](https://plato.stanford.edu/entries/russell-paradox/) of Russell's Paradox. In general, I've found the Stanford Encyclopedia of Philosophy to have some of the most clear and concise explinations of abstract concepts. There's some other paradoxes that arise in math that could probably be categorized as strange loops, but they got too abstract for me to understand.

Going off on a tangent, but here's some other great pages from the Encyclopedia of Philosophy.
* [Uncertainty Principle](https://plato.stanford.edu/entries/qt-uncertainty/)
* [Cellular Automata](https://plato.stanford.edu/entries/cellular-automata/)

#### Mobius Strips & Other Topological Shapes*
It's hard to say if topological shapes like the Mobius strip or [Klein bottle](https://www.youtube.com/watch?v=-k3mVnRlQLU) are strange loops. While the definition is loose, I think a key idea of strange loops is to be traversing through a hierarchical system. The primary reason why I believe both the Mobius strip and Klein bottle are strange loops is because due to their "non orientable" property -- as you traverse along the surface, your orientation is montonically moving in one direction yet you end up at the same location. In this sense, a strange loop occurs.  


<div style="display: flex; justify-content: center; text-align: center;">
    <div class="image" style="display: inline-block; margin-right: 20px;">
        <img src="/assets/img/strangeloops/klein.jpg" width="500"/>
        <p>Klein Bottle</p>
    </div>
</div>

## Loops vs Strange Loops 
I originally had "boostraping and compilers", "recursive AI learning", and a few other examples as topics under the strange loops section. But as I was writing, it felt wrong. Strange loops are unexpected, and the examples mentioned make progress in their task leading to a result that's different from the input. I'm uncertain that some of the examples in the strange loops category are not being conflated with normal loops (especially the natural language examples). But normal or strange, loops are everywhere -- train routes, earrings, cereal, control systems, the list goes on (and maybe comes back around). When I was first writing this, I put down a lot of half-completed musings in this section, but upon looping back, many of these were able to be cut out without any loss in substance. 


<div style="display: flex; justify-content: center; text-align: center;">
    <div class="image" style="display: inline-block; margin-right: 20px;">
        <img src="/assets/img/strangeloops/Bagels-4.jpg" width="500"/>
        <p>We all thought sliced bread was good until this toroidal beauty came into the picture (search term here was "topological bread")</p>
    </div>
    <div class="image" style="display: inline-block; margin-right: 20px;">
        <img src="/assets/img/strangeloops/rabbitclock.png" width="500"/>
        <p>Even time, which seems like the last thing that should be playing with the spooky world of loops is represented as a circle.</p>
    </div>
     <div class="image" style="display: inline-block;">
        <img src="/assets/img/strangeloops/camshaft.jpg" width="500"/>
        <p>A cam shaft converts piston motion to circular motion so that a car can drive forward.</p>
    </div>
     
</div>

# Ronald McDonald and other stylish figures 
Now for a deviation in the topic of loops -- branding. As well as being a place to share and think about ideas, the Strange Loops platform is also an experiement in creating a brand. I recently had a discussion about the importance of brands. My brother was suprised to find out that the wealthiest person in the world (a few weeks ago from writing this) was not Jeff Bezos, Elon Musk, or Bill Gates but Bernard Arnault, the CEO of LVMH -- a conglomerate company that owns luxury goods like Louis Vuitton, Tiffany & Co., and other stores found in the duty-free section of airports in which items like suglasses seem like they're meant to be examined but not purchased. Anyway, it was a good reminder that the power of brands is real. I remember a few years ago, one of my teachers once showed our class the following advertisment:


<div style="display: flex; justify-content: center; text-align: center;">
    <div class="image" style="display: inline-block; margin-right: 20px;">
        <img src="/assets/img/strangeloops/mcdonalds.jpg" width="500"/>
        <p>I'm lovin' it</p>
    </div>
</div>


Even though the word "McDonalds" or the entire M shaped logo, everybody in the class recognized it as a McDonalds ad at once -- it's interesting and maybe a bit spooky to think that the red with a splash of gold is instantly associated with McDonald's. It's of course absolutely ridiculous to compare the "brand" of Strange Loops to LVMH or McDonalds, empires where the sun never really does set. Nevertheless, its been fun to start consolidating some ideas under an umbrella name, choosing a logo, and thinking about how Strange Loops appears from an outside perspective. I also like thinking about how strange loops (or normal loops) could be sprinkled throught the blog or even baked into the architecture of the website using things like recursive navigation (although I think this may send shudders down any user experience or interface designer's spine). 

# Conclusions 
- Strange loops occur when traversing a singular direction through a hierarchical systems and yet somehow winding back up at the same origin.
-  Along the way of writing this introductory post, some interesting topics that I'd like to investigate came up that didn't quite fit into this post. 
    - Riemann surfaces
    - Peano curves and space filling curves in general
    - Real world applications of Mobius Strips
    - Mathematical origami
- Writing this post: problems and solutions
    - **Problem**: Deciding what to include and what to leave out. Many many things were cut because they didn't fit the theme of the post or were so semi formed that it seemed better to leave them out.
        - **Solution**: It seems like moderation is needed here. Saying each little thought is detracting to the post, but censoring too much defeats the purpose of thinking and learning in public. 
    - **Problem**: Getting caught up in the details.
        - **Solution**: Leveraging abstraction. Need to start erring on the side of less wikipedia spirals.  
    - **Problem** Regurgitating information versus understanding and using information.
        - **Solution**:
            - Mixing theory with practice. It's easy to get caught up in the theory of things and forget to actually do things. I feel that blogging is somewhat inbetween theory and practice. 
            - Don't google or chat gpt it -- think. I'm very conditioned to searching things up on Google (or in recent times, ChatGPT) without taking a moment to think about a problem. Solutions on demand are like pool noodles -- addicting, but in the end, gotta learn how to swim. 
            - Linking to outside resources. When first writing this post, I rephrased a lot of the information I had read, but going back through, I realized that linking to the original source is much more efficient and also gives credit where credit is due.
            - Recognizing that most content won't be novel and that's ok. 


### ```jmp intro  // ;)```

Cheers and thank you for reading 🌺,

Aloha