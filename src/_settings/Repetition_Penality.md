---
tags: [settings]
icon: dot
title: Repetition Penality
order: 100000000000
---
`Repetition Penalty` is a setting used to control how often the model repeats certain words or phrases in the generated output. When the repetition penalty is set to a higher value, the model is less likely to repeat the same word or phrase multiple times in the output.

### Repetition Penalty Range
If set higher than 0, repetition penality only applies to the last few tokens of the story rather than to the entire story. The slider controls the amount of tokens at the end of your story to apply it to.

### Repetition Penalty Slope
If both this setting and `Repetition Penality Range` are set higher than 0, the repetition penality will be apply more strongly on tokens that are close to the end of the story. High values will result in the repetition penalty difference between the start and the end of your story being more apparent.