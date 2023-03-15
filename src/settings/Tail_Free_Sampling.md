---
tags: [settings]
icon: dot
title: Tail Free Sampling
order: 100000000000000
---
`Tail Free Sampling` is a setting used to improve the consistency of the generated output. When generating new text, the model can use Tail Free Sampling to select the next word, but with less emphasis on the rare or extreme values.

The slider is a tool that allows you to adjust the amount of Tail Free Sampling used by the model. When you pick a higher value, the model will be more likely to avoid selecting the rare or extreme values, which can help to increase the consistency of the generated output. This is because the model will be working from the bottom of the probability distribution, selecting more common and likely values and trimming the lowest probability tokens.
