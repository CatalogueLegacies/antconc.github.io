---
title: "Word lists"
teaching: 10
exercises: 10
questions:
- "What are word lists in AntConc and when would you use it?"
- "How do word lists work in AntConc?"
- "How might I interpret word lists generated from catalogue data?"
objectives:
- "Explain what word lists are in AntConc"
- "Use word lists to start identifying the lingustic character of a corpus"
keypoints:
- "Word lists are a way of getting an overview of the lingustic features of a corpus"
- "AntConc provides a number of options for presenting word lists"
- "When using AntConc to count things, we need to be mindful that machine readable strings are not the same as human readable words"
- "Outputs from AntConc queries can be saved locally as text files"
---

## Word lists
A word list counts how many times each word occurs in the selected text(s). Generally, in a word list we expect the most frequent words to be function words, e.g. for English-language texts, words like "the", "of", "and", "but", etc. However, for texts that are restricted by topic, genre and/or text type - which we would expect descriptive text in catalogue data to be - then the order of these words can vary and there will also be domain-specific vocabulary.

Word lists then are a useful starting point for getting an overview of the lingustic features of a corpus. For example, if you have a corpus that includes minor variations in data values - e.g. names of people, organisations, places, classification terms - creating a word list can be an effect way of spotting those variants.

## Making a word list
To use the 'Word List' function in AntConc, click on the `Word List` tab and press `Start`.

Antconc then returns the following information:
- The total number of words in the corpus (`Word Tokens`).
- The total number of unique words in the corpus, which is the vocabulary size of the corpus (`Word Types`).
- A ranking of every unique word type by its frequency in the corpus.

You will note that AntConc has treated all text as lowercase. Whilst this can be useful, it means that the word "cook" and the family name "Cook" are treated as the same `word type` in our count. Case sensitivity is also useful when examining curatorial voice, because knowing where words are used in relation to punctuation is a tell for features like sentence structure and length.

In AntConc you need to change case sensitivity settings for each tool individually. Change this now by going to `Tool Preferences`, choosing `Word List`, and unticking `Treat all data as lowercase`, and then pressing `Apply`. Back in the `Word List` tab hit `Start` again to see the difference.

> ## What is a word?
>
> Note here that depending on your dataset, an important setting is `Token Definition` under `Global Settings` (found in the top navbar). This defines what AntConc sees as a word, e.g. you need to specify that numbers, punctuation characters and symbols can be part of words in order for AntConc to see things like urls or other special characters that provide meaning (e.g. hashtags in tweets).
{: .callout}

## Interacting with a word list
There are a number of ways in which you can interact with your word list output:

First, turning to the `Freq` column you can select and highlight frequency values. If you click on an individual word, AntConc will move to the `Concordance` tab and plot a 'concordance' for that word: that is, a list that shows sentences that contain the word you clicked on. To test this choose a lower frequency word (ranked below 1000), click on it, and AntConc will move to the `Concordance` tab. We will look at concordances in the next episode. For now, move back to the `Word List` tab and observe that your results haven't been lost.

Second, you can re-sort the output in the `Word List` tab using the options in the `Sort by` area. By default sorts in the `Word List` tab are set by rank, meaning that the most common word type is shown at the top, and the least common word type is shown at the bottom. For example, the sort can be inverted by ticking `Invert Order` and pressing `Start`. Note that you are now presented with a long tail of infrequently used word types.

The sort can also be changed so that rather than sorting by the frequencty of words, the sort is made by the words themselves, listed in alphabetical order. To do this, untick `Invert Order`, select `Sort by Word` in the dropdown and hit `Start`. Browsing through an alphabetical sort can be a useful way of finding errors in the data (e.g. stray punctuation), spelling mistakes, variations in capitalisation, or - thinking of curatorical voice - different lemma forms of words.

> ## Is AntConc thinking or has it crashed?
>
> AntConc can often become non-functional. In most cases the software is processing your request rather than fallen over. For example, when looking at a word list it is ill-advised to click on a very frequent word as AntConc may take a while to process the concordance for that word. Of course, if a very frequent word is one your interested in, you'll just have to be patient!
{: .callout}

## Saving your output
To save the output from your `Word List` go to the `File` menu in the navbar and select `Save Output`.

> ## Good practice when saving outputs
>
> All tabs in AntConc provide the option to save the output. This is vital for keeping a record of your findings. Note that the default output is a file called `antconc_results.txt`. As this contains no information about your corpus, your query, your settings, or what version AntConc you are using, you are encourged to note that information seperately.
{: .callout}

## Tasks
Having learnt about the `Word List` tab in AntConc, work in pairs or small groups on the following challenges.

>## Task 1: What % of all word tokens are accounted for by the 30 most common word types?
>* Use the `Word List` tab to count all word types and then use the output to make an estimate. Note: you may need to do some calculation outside of AntConc.
>
>>## Solution
>>
>>1. Remove any text from the search box, select `Sort by Freq` and hit `Start`.
>>2. Observe the figure of `1236723` word tokens. Select the frequency values of the 30 most common word types, paste them into a spreadsheet programme, and sum them. You should get `522433`. Use these two figures to calculate a percentage: `(522433/1236723) x 100 = 42.24%`
>>>* It is common in English language corpora to find that roughly half the corpus is accounted for by a small number of frequent words. This observation goes a long way to explaining way corpus linguists often present and work with lists of ‘top’ words (not that word lists are the only tool in the corpus linguists armoury, as we shall see!)
>{: .solution}
{: .challenge}

>## Task 2: What might the variant uses of the verb "enter" infer about language use in the dataset as a whole?
>* Use the `Word List` tab to count all word types, then use the sorting options to help you navigate to variants of the verb "enter" and their use in context.
>
>>## Solution
>>
>>1. Remove any text from the search box, select `Sort by Word` and hit `Start`.
>>2. Browse to the string "enter". There are five word varients of "enter" with frequencies as follows:
>>>* Enter: 1
>>>* enter: 54 (sum of "enter", "enter," and "enter.")
>>>* entered: 25 (sum of "entered," and "entered")
>>>* entering : 18 (sum of "entering" and "entering.")
>>>* enters:  110 (sum of "enters", "enters," and "enters."
>>3. Note the lack of entries in the past tense form ("entered") and the active present participle form ("entering"). Instead the third-person present form dominates, used in speech to refer to individuals, such as in "She enters", "Samir enters", or "Gene enters".
>>4. "Enter" can also be used in both the plural present form - "they enter" - and the future tense form - "He/She/It/You/We/They will/shall enter" - so we need to check which usage is most common in the corpus. To do this, click on the word form "enter" and look at the output in the `Concordance` tab. Note that the output shows a predominant use of the present tense form of "enter", such as in "who enter from the left", "are about to enter it", "tries to enter through a door".
>>5. What we can conclude then is that the verb "enter" is used largely in the present tense. We can infer - pending further investigation - that the curatorial descriptions in the corpus describe what is in front of the curator rather than, for example, describe the life of the object or its principle characters.
>{: .solution}
{: .challenge}

>## Task 3: Find the variants of the word "behind" and estimate their use relative to each other. Without looking at the concordances for these, discuss what hypotheses might explain this result.
>* Use the `Word List` tab to count all word types and then use the output to make an estimate. Note: you may need to do some calculation outside of AntConc.
>
>>## Solution
>>
>>1. Remove any text from the search box, select `Sort by Word` and hit `Start`.
>>2. Browse to the string "behind". There are two word variants in the corpus: "behind" and "Behind". Their use is roughly 50/50 (with slightly more uses of "behind").
>>3. In most cases, "Behind" would be used at the start of a sentence. With this capitalised form accounting for roughly half of the total uses of the word "behind", we can infer a series of possible hypotheses (with increasing uncertainty) about the corpus:
>>>* The word "behind" is used often at the start of a sentence.
>>>* Postitional/spatial words might frequently be used at the start of sentences.
>>>* The high frequency of capitalised variants of prepositions, like "behind", could indicate the presence in the corpus of many short sentences (because frequent capitalisation of prepositions may be an indicator of short sentence length).
>{: .solution}
{: .challenge}
