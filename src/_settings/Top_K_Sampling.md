---
tags: [settings]
icon: dot
title: Top K Sampling
order: 1000000000000000
---
When using "top k", you select the top $k$ most likely words to come next based on their probability of occurring, where $k$ is a fixed number that you specify.

For example, if you set `Top_K` to 5, the language model will only consider the five most likely words to come next, rather than all the words in its vocabulary.

You can use `Top_K` to control the amount of diversity in the model output. By limiting the selection to a small number of the most likely words, the language model can produce more predictable and conservative text. However, by increasing k, you can allow for more unexpected and creative choices in the generated text.

Overall, `Top_K` can be useful for balancing the tradeoff between predictability and creativity in language model output.


### Combining `Top_K` with `Top_P`

Combining `Top_K` and `Top_P` is a technique called nucleus sampling or Top_P sampling with Top_K cutoff. This technique allows you to use both methods together to generate even more diverse and interesting text.

Here's how it works: first, the model uses `Top_p` to select the most likely words up to a certain cumulative probability threshold, as explained in the [`Top_P` page](https://docs.alpindale.dev/pygmalion-docs/settings/top_p)

 Then, it applies a `Top_K` cutoff to this set of words, selecting only the top k most likely words from the `Top_P` selection.

By using both techniques together, you can generate text that is both diverse and controlled. The `Top_P` selection ensures that the language model has the freedom to choose from a range of plausible words, while the `Top_K` cutoff limits the number of choices to a manageable set of highly likely words.

The specific values of `Top_P` and `Top_K` can be adjusted to achieve different levels of diversity and control in the generated text. For example, a higher `Top_P` value will allow for more diverse choices, while a lower `Top_K` value will provide more control over the output. It's important to experiment with different settings to find the right balance for your specific use case.
