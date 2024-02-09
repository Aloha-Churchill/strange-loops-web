---
layout: post
title: Discovering Data Cmpresn
subtitle: Or how we can store War and Peace on a device smaller than Tolstoy's pinky toe 
cover-img: /assets/img/BLOG_COVERS/A.jpeg
thumbnail-img: /assets/img/BLOG_THUMBNAILS/16_crow.jpg
tags: [math, computer science]
---

## What is data compression?
Wikipedia (the free encyclopedia, not to be confused for the another Wikipedia) defines data compression as the “process of encoding information using fewer bits than the original representation.” Data compression tries to maintain as much information with as small of a representation as possible, and that’s what I’ll be trying to learn about here. Data compression can be lossless (reconstructable) or lossy (can’t recover original).

## Lossless Data Compression
### Huffman Encoding
Lossless algorithms exploit redundancy. A common technique that’s used in lossless compression is Huffman Encoding. Instead of having each character represented by a fixed length code, the encoding length is based on the frequency which characters appear. Intuitively, more frequent characters should get shorter encodings. The question becomes: How do we create a code that is uniquely decodable and the shortest average length given a frequency distribution? For a great explanation of how this was solved by Huffman, I’d highly recommend watching [this video](https://www.youtube.com/watch?v=B3y0RsVCyrw) from 16:44. Essentially, Huffman had the idea to build a tree, where each node was a character with it’s probability. He put the least frequent characters at the bottom of the tree, iterated this process in a clever way, and would end up with the most frequent character on the top of the tree. Then, he simply assigned the top character a 1 or 0, and then for each child node appended a 1 or 0 depending on if it was to the left or right. 

<div style="display: flex; justify-content: center; text-align: center;">
 <div class="image">
    <img src="/assets/img/data/huffman.png" width="500"/>
</div>
</div>


### Grammar-based codes
Many famous compression lossless compression methods are classified as “grammar-based codes”. Sealing my fate for at least another hour, I clicked on the link to the grammar based codes page.   

The page on Grammar-based code was a small little article, in the dregs of Wikipedia. Immediately, I was surprised to see the phrase “Context Free Grammar”. I had only ever encountered Context Free Grammar (CFG) when learning about compilers and constructing programming languages, but it turns out that the idea of CFGs is helpful in data compression. The idea of a CFGs is to create a set of rules that can generate a set of strings. Somebody had the clever insight that if they first created a context free grammar for a given data sequence, they could then send the CFG rules to create the data sequence instead of the original sequence. Given this, the task becomes to try and find the smallest CFG possible to describe a data sequence, which turns out to be an NP-hard problem! Once a CFG is determined, we can then apply Huffman encoding to the rules instead of the data itself. What is finally sent is the Huffman encoded sequence of rules that generates the original data. 

An alternative to Huffman?! Welcome to arithmetic coding 
Despite it’s fame, Huffman encoding schemes are not always the most efficient way to encode data! Let’s take a look at this example directly from Wikipedia:

Let A, B, C all be symbols that are equally likely to occur. A traditional Huffman encoding would assign something like A=00, B=01, and C=10, with 11 unused. So that no combinations are wasted, let’s instead represent the symbols in base 3, where A=0, B=1, C=2. Now encode ABBCAB. Using the traditional method, we’d have 000101100011. Using our ternary method, we have 011201, which we can then turn back to binary where 0=00, 1=01, 2=11 to get 0010110001 which saves 2 bits. 

So how do we generalize this method? The idea is that each codeword given a set of probabilities, can be represented as a unique rational numbers in the range 0-1. Again, YouTube to the rescue – there’s not too many videos on arithmetic coding but here’s a pretty good runthrough of an example that illustrates the [idea](https://www.youtube.com/watch?v=-R2a2a1-2MM). 


<div style="display: flex; justify-content: center; text-align: center;">
 <div class="image">
    <img src="/assets/img/data/arithmetic.png" width="500"/>
</div>
</div>



So now, when you encounter somebody who tends to repeat things, an approach to confront them might be to say, "what you are saying seems to be highly compressible." This is perfect, because then they'll be able to poke a bit of fun at you as well for being rather a nerd about things.


### Lossy Data Compression
Lossy algorithms tend to be more complex and in addition to eliminating redundancy, also use the way humans perceive information to extract the most important parts of different data types. Probably the most famous example of this is JPEG compression which primarily exploits two interesting things about our visual system: first, human’s are more sensitive to luminance than color, second, humans can’t perceive high frequency variation at a pixel level. In order to exploit the second point, the JPEG format uses the discrete cosine transform.  

[This video](https://youtu.be/0me3guauqOU?si=E8AL2JiJKF1fk8d_) on the DCT has an excellent explanation of how it works. Here, I’ll try and capture some of my main takaways and realizations from watching the video.

* The basic idea of the DCT is to represent a signal as a sum of individual cosine waves. 
* Each cosine wave represents different frequencies of pixel brightness patterns (how fast they change).
* The DCT works by taking the dot product, or similarity between a known cosine wave and the current sample. This is because dot products measure similarity between two vectors. In this case, our vectors are the sampled points on the cosine and the signal. 
* Each of the 8 frequencies corresponds ot a different pattern of brignesses. All combinations of 8 pixel values can be represented by the 8 cosine waves.
* In the two dimensional case, you can take 8x8 blocks and apply the DCT to the rows and then columns of the blocks, ending up with an 8x8 grid of coefficients, each which correspond to a different pattern.
* JPEG takes out the higher frequency DCT components since it’s hard for humans to perceive these
* It’s useful to compare against cosine waves because this family of functions is periodic, and so gives information about frequency (and amplitude and phase, so some bonus points there). 

## Questions and Potential Investigations
* Within the DCT, we’re representing a signal with cosine waves which, by it’s nature, gives information about frequency. Are there other families of functions to sample from? What would this tell us about a particular signal?
* Higher dimensional DCT applications. Someone was describing how higher dimensional DCT’s could be used to solve problems like determining weather conditions with lasers. 
* Are there types of data where you’d want to highlight high frequency components? Stocks, sound files, genetic data – might be interesting to look at.
* What are key differences between the DCT and DFT (Discrete Fourier Transform)? Why would you use one over the other?
My brother was wondering something very interesting: does the brain compress information and how does the brain store the information? Does this mean that it represents information in a graphical structure made up of neurons? It’s clear that our brain doesn’t work like the DCT, and actively filter out these lower frequency components or work at a “pixel” level, so the core question becomes, how does it store information and can we exploit this? 
   * Link on article of how scientists currently believe how memories are formed: https://qbi.uq.edu.au/brain-basics/memory/how-are-memories-formed#:~:text=In%20other%20words%2C%20recalling%20a,changing%20the%20connections%20between%20neurons. 
