---
tags: [settings]
icon: dot
title: Top A Sampling
order: 1000000000000
---
`Top A Sampling` is a way to pick the next word in a sentence, based on how important it is in the context. We use a "leader" number between 0 and 1 to help us decide which words are most important.

Let's say we have a sentence and the model needs to predict the next word. The model looks at all the possible words and how important they are based on how often they appear in similar sentences in its training data.

With `Top A Sampling`, we only look at the most important words, based on the leader number. For example, if the leader is 0.8, we only look at the top 80% of the most important words to make our prediction.

Overall, `Top A Sampling` with a leader helps us make better predictions by focusing on the most important words while still allowing for some level of randomness and creativity in the generated text.