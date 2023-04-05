---
tags: [settings]
icon: dot
title: Top A Sampling
order: 1000000000000
---
`Top A Sampling` is a way to pick the next word in a sentence based on how important it is in the context. We use a "leader" number between 0 and 1 to help us decide which words are most important.
Top-A considers the probability of the most likely token, and sets a limit based on its percentage. After this, remaining tokens are compared to this limit. If their probability is too low, they are removed from the pool.
Increasing A results in a stricter limit. Lowering A results in a looser limit.

This means that if the top token has a moderate likelihood of appearing, the pool of possibilities will be large. On the other hand, if the top token has a very high likelihood of appearing, then the pool will be 1-3 tokens at most. This ensures that structure remains solid, and focuses creative output in areas where it is actually wanted. 
