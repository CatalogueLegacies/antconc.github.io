---
title: "Wordlists"
teaching: 10
exercises: 10
questions:
- "What are wordlists in AntConc and when would you use it?"
- "How do wordlists work in AntConc?"
- "How might I interpret wordlists generated from catalogue data?"
objectives:
- "Explain what wordlists are in OpenRefine"
- "Use wordlists to start identifying the lingustic character of a corpus"
keypoints:
- "Wordlists are a way of getting an overview of the lingustic features of a corpus"
- "AntConc provides a number of options for presenting wordlists"
- "When using AntConc to count things, we need to be mindful that machine readable strings and are not the same as human readable words"
- "Outputs from AntConc queries can be saved locally as text files"
---

## Wordlists
A word list counts how many times each word occurs in the selected text(s). Generally, in a word list we expect the most frequent words to be function words, e.g. for English-language texts, words like `the`, `of`, `and`, `but`, etc. However, for texts that are restricted by topic, genre and/or text type - which we would expect descriptive text in catalogue data to be - then the order of these words can vary and there will also be domain-specific vocabulary.

Word lists then as a useful starting point for getting an overview of the lingustic features of a corpus. They are very effective where you have a corpus with minor variations in data values, e.g. names of people, organisations, places, classification terms.

### Making a word list
To use the 'Word List' function in AntConc, click on the `Word List` tab and press `Start`.

Antconc then presents a returns the following information:
- The total number of unique words in the corpus (`Word Tokens`).
- The vocabulary size of the corpus (`Word Types`).
- A ranking of every unique word type by its frequency in the corpus.

> ## What is a word?
>
> Note here that depending on your dataset, an important setting is `Token Definition` under `Global Settings` (found in the top navbar). This defines what AntConc sees as a word, e.g. you need to specify that numbers, punctuation characters and symbols can be part of words in order for AntConc to see things like urls or other special characters that provide meaning (e.g. hashtags in tweets).
{: .callout}

You will note that AntConc has treated all text as lowercase. This should be changed when examining curatorial voice, because knowing where words are used in relation to punctuation is a tell for features like sentence structure and length. In AntConc you need to change these settings for each tool individually. Change this now by going to `Tool Preferences`, choosing `Word List`, and unticking `Treat all data as lowercase`, and then pressing `Apply`. Back in the `Word List` tab hit `Start` again to see the difference.

## Interacting with a word list
There are a number of ways in which you can interact with your wordlist output:

First, turning to the `Freq` column you can select and highlight frequenct values. If you click on an individual word, AntConc will move to the `Concordance` tab and plot a 'condordance' for that word: that is, a few that shows sentences the contain the word you clicked on. We will look at concordances the next episode. For now, move back to te `Word List` tab and observe that your results haven't been lost.

> ## Is AntConc thinking or has it crashed?
>
> AntConc can often become non-functional. In most cases the software is processing your request rather than fallen over. For example, when looking at a word list it is ill-advised to click on a very frequent word as AntConc may take a while to process. Of course, if a very frequent word is one your interested in, you'll just have to be patient!
{: .callout}

Second, you can re-sort the output in the `Word List` tab using the options in the `Sort by` area. By default sorts in the `Word List` tab are set by rank, meaning that the most common word type is shown at the top, and the least common word type is shown at the bottom. For example, the sort can be involved by ticking `Invert Order` and pressing `Start`. Note that you are now presented with a long tail of infrequently used word types.

The sort can also be changed so that rather than sorting by the frequencty of words, the sort is made by the words themselves, listed in alphabetical order. To do this, untick `Invest Order`, select `Sort by Word` in the dropdown and hit `Start`. Browsing through an alphabetical sort can be a useful way of finding errors in the data (e.g. stray punctuation), spelling mistakes, variations in capitalisation, or - thinking of curatorical voice - different lemma forms of words.

## Saving your output
To save the output from your `Word List` go to the `File` menu in the navbar and select `Save Output`.

> ## Saving outputs
>
> All tabs in AntConc provide the option to save the output. This is vital for keeping a record of your findings. Note that the default output is a file called `antconc_results.txt`. As this contains no information about your corpus, your query, your settings, or what version AntConc you are using, you are encourged to note that information seperately.
{: .callout}

>## Use Clustering to clean up author data
>
>1. Split out the author names into individual cells using `Edit cells -> Split multi-valued cells`, using the pipe ( \| ) character as the separator
>2. Choose `Edit cells -> Cluster and edit` from the 'author' column.
>3. Using the `key collision` method with the `fingerprint` Keying Function, work through the clusters of values, merging them to a single value where appropriate
>4. Try changing the clustering method being used - which ones work well?
{: .challenge}

>## Find all entries without a photographer name
>* If we accept that Column 8 lists the surnames of photographers, use the `Facet by blank` function to find all photographs in this data set without a named photographer
>
>>## Solution
>>
>>1. On `Column 8` drop down and select `Customized facets > Facet by blank`
>>2. `True` means that it is blank, so you can:
>>    * Select `include` on True in the facet to filter the list of lines on Column 8 that don't have a family name (4524 rows).
>{: .solution}
{: .challenge}
