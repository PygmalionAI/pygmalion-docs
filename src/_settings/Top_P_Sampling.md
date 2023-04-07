---
tags: [settings]
icon: dot
title: Top P Sampling
order: 10000000000000000
---
`Top_P` is a way of generating text with an AI model that helps to make the output more diverse and interesting. When using `Top_P`, you select the most likely words to come next based on their probability of occurring, but only up to a certain cumulative probability threshold. This means that instead of always selecting the most likely word, the language model can choose from a wider range of words that are still reasonably likely to occur.

For example, if you set `Top_P` to 0.5, the language model will only consider words that make up the top 50% of the probability distribution for the next word, rather than just the most likely word.

You can can use `Top_P` to make the model output more varied and creative. By not always selecting the most likely word, the language model can surprise you with unexpected but still plausible words, creating more interesting and engaging text.
