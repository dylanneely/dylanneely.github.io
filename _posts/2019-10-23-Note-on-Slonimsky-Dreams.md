---
layout: post
title:  "Note on Slonimsky Dreams"
---

Slonimsky Dreams is a playful take on Nicolas Slonimsky’s invaluable, idiosyncratic and pedantic volume, *Thesaurus of Scales and Melodic Patterns*. The book contains 1,330 numbered scales, plus additional progressions, scales, arpeggios, harmonizations and canons. They are arranged according to a system of his own invention, which is both eccentric and internally logical. His intention was to allow composers  to use the book as a thesaurus. So, for example, if I were in search of a scale that uses the minor sixth as its foundational interval and comprises six notes per two octaves, I could flip to the “Quadritone Progression” section, which provides a set of scales that symmetrically divide two octaves into three parts, and peruse the scales provided under “Interpolation of One Note”. If I wanted to move on to twelve-notes-per-two-octaves scales, I could jump ahead to “Interpolation of Three Notes”. Of course, in such specific scenarios the whole thing seems ridiculous, but in a broader sense - for example, playing through all whole-tone scale variations while searching for the right inflection of mystery - the book’s organization is intriguing, original, and occasionally useful. By increasing the complexity within each section through the interpolation of additional notes, and treating those interpolations according to widening intervals, there is a hypnotic, authorial patterning more interesting than most books of scale studies.

My generative composition is built on top of the “Performance RNN” browser demo, which was created by Magenta, a research team at Google. RNN stands for recurrent neural network, one of the artificial neural network variants used in machine learning. Performance RNN was trained with musical data (MIDI) from the Yamaha e-Piano Competition, which comprises contestant performances captured by the Disklavier. There is a heavy emphasis on romantic piano literature, with composers represented from the 17th to 20th centuries, and this training bias is clear in the AI’s continuous generative output. To my ear, the breakthrough in this model is the lack of time quantization, which provides a human-adjacent quality of temporal flow.

As interesting as Google Creative Lab’s interactive AI demos can be, they are pedagogical by nature. Playing with them is often an exercise in testing their efficacy or limits. I wanted to get away from perspectives that tend to either be exceedingly analytical (for example, finding errors in AI-generated fugal counterpoint) or naively astonished. (Mis)using technology as composers have always done, I desired to move the experience into the realm of the aesthetic. Slonimsky’s scales provide a harmonic template of continuous change, as well as a modernist slant toward atonality that creates tension with the tonal predisposition of the model’s training. I eliminated entirely the interactive user interface of the demo, replacing it with a Perlin noise visualization, whose color and shape change in response to the musical content.

The piece’s harmonic origin is determined by the time of the day. So, for example, if a visitor accesses the site at 12pm local time, they will begin on the 665th scale, midway through the collection. Once started, the piece cycles through the entirety of the scales every twelve hours. The model generates notes continuously in real-time, which are conditioned by the pitch set of the current Slonimsky scale. The piece will never repeat itself or end. I’ve intended it as a tribute to the incomparable Nicolas Slonimsky, who is best remembered for his Lexicon of Musical Invective. Perhaps you will feel about this piece as the Boston Gazette felt about Brahms: “It is mathematical music evolved with difficulty from an unimaginative mind.” Or, as the Daily Mail wrote of Schoenberg: “If music at all, it is music of the future, and we hope, of a distant one.”



## Acknowledgements

The underlying neural network code, as well as its relationship to the sampled piano output, is taken verbatim from the Performance RNN model ported to Typescript:

Ian Simon and Sageev Oore. "Performance RNN: Generating Music with
Expressive Timing and Dynamics." Magenta Blog, 2017. https://magenta.tensorflow.org/performance-rnn

https://tensorflow.github.io/magenta-js/music/index.html

Thank you to Alex Nathanson for the suggestions and assistance with the visualization.

Thank you to Alexander Holm for the Salamander Grand Piano samples.

Thank you to Adam Roberts, Curtis Hawthorne, Tero Parviainen, Monica Dinulescu, and everyone else on the Magenta and Magenta.js team, for their helpful tutorials and demos, and clear documentation.

"Lexicon of Musical Invective", Nicolas Slonimsky, University of Washington Press, 1969.

"Thesaurus of Scales and Melodic Patterns," Nicolas Slonimsky, Charles Scribner's Sons, 1947.
