---
order: 1
icon: question
title: FAQ
---

# Frequently Asked Questions

### My character has terrible memory!
This could be due to the limited context size. Pygmalion 6B has a maximum context size of 2048 [tokens](https://en.wikipedia.org/wiki/Lexical_analysis#Tokenization). This includes your character description, example messages, and all your chatlogs. The description and examples are placed at the top of the context memory - all your subsequent chat logs are placed beneath them. This means that if your character description + examples chats are 400 tokens, you'll only have 1648 tokens left for your messages. The bot will forgot everything past those 1648 tokens.

Character editors/creators such as TavernAI's will give you a token count for your character, but you can also use OpenAI's tokenizer service.

[!ref OpenAI Tokenizer](https://platform.openai.com/tokenizer)

### My character's responses are too short!
The character will mimic the example chats and greeting message's style. Keep these in mind if you want to create a verbose character:
- Descriptive and verbose greeting message and example chats.
- Descriptive and verbose responses by the user (you!).
- Re-generate the response until you see a satisfactory one.
- Manually edit the character's response to make it more verbose.

### My character is generating nonsense!
Your Temperature or Repetition Penalty settings are likely too high. The recommended range for Temperature (for chatbots) is between `0.5` to `0.9`. The range for Repetition Penalty is between `1.1` to `1.2`.

