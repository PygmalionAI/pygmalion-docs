---
tags: [settings]
icon: dot
title: WI (World Info) Depth
order: 10000000
---
Number of actions (Input/Output) from the end of the story to scan for World Info keys.

Excerpt from the KoboldAI wiki:

:::
<style>
    .sample {
        text-align: center;
        color: #ffffff;
        border-radius: 10px;
        background-color: #55575b;
        border: 3px solid #000000;
        padding-top: 20px;
        margin-bottom: 20px;
    }
</style>
:::
:::sample
World Info is where you can flesh out the details of your wider world. The engine will help conserve tokens in your context by only inserting World Info entries when their keywords are mentioned in the actual story text. However, they are inserted toward the top, after the Memory but before the actual story text, so they have a moderate effect on what the AI generates.

World Info entries are like an encyclopedia entry, providing a succinct overview of the most relevant information about whatever topic - characters, species, places, items, etc...

The AI doesn't see the key word or title of the World Info entry "behind the scenes", so the actual text should be an entirely self-contained description. For example, if you have a World Info entry titled "Director Abrams", the entry should say "Director Abrams is the executive and governor of the colony" rather than just "the executive and governor of the colony", because the AI will only see the entry.

Use World Info entries that cross reference each other appropriately to create a more dynamic and interactive world. If your "combat android" World Info entry mentions that they carry plasma rifles, then create a short "plasma rifle" entry separately. If you create a "Admin Tower" entry that mentions containing a command center, computer core, and offices, create distinct "command center", "computer core", and "offices" entries that mention being located in the Admin Tower.

It helps to use many key words that might pull in a World Info entry whenever it might be appropriate, rather than just its proper name(s).

If you have a rich tapestry of interconnected World Info entries with many relevant keywords, you may find that multiple World Info entries are getting pulled into the context at any given time. So it's good to keep them fairly short (50 tokens for minor stuff, 100 tokens for significant characters, no more than 150 for major keystones of the setting).
:::