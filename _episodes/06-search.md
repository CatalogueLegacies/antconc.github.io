---
title: "Search"
teaching: 10
exercises: 10
questions:
- "How do search in AntConc?"
- "How can I use search to discover features of catalogue data?"
objectives:
- "Explain how to search"
- "Explain how to read a concordance"
keypoints:
- "You can search a corpus in AntConc using free text and wildcards"
- "Carefully changing the search settings enables you to build better queries"
- "AntConc can be used for making both rough estimates of lingustic features within a corpus, as well as collecting precise data"
---

## Searching in AntConc
After generating lists that characterise a whole corpus, the other main way to interact with a dataset in AntConc is to use search to narrow your enquiry to a subset of a corpus.

The `Concordance` tab is one many that responds to search. Navigate to the `Concordance` tab, put the string "wear" into the search box, and hit `Start`.

After a little thought, AntConc populates the tab. We can observe that - by default - a search in the `Concordance` tab does a number of things:

- It prompts AntConc to tell us how many times the search term has matched in the corpus.
- It looks for the search term as a word rather than as a string of characters (so our hit count is for *words* not *strings*).
- It uses a case-insensitive search.
- It assumes we care more about the word next *after* the search term rather than *before* it.
- It sorts the results alphabetically by the first character after the search term.
- For each line, it returns information on the file name from which the search term orginates. That is, whilst we’ve separated our file into parts to ease import and processing, you should be able to see there is comparative potential here.

> ## Compartive analysis in AntConc
>
> By working on multiple files, and providing outputs that identify which result relates to which file, the `Concordance` tab gives us a way into comparative analysis of catalogue data, be that longitudinal (files seperated by the decades in which catalogue entries were made), by collection, or be catalouger. We discuss comparing corpora in more detail in a [later module](https://cataloguelegacies.github.io/antconc.github.io/09-comparing/index.html).
{: .callout}

You can then drag and drop column names to re-order the columns, or remove columns completely if they are not required.

## Renaming columns

You can rename a column by opening the drop-down menu at the top of the column that you would like to rename, and choosing 'Edit column' > 'Rename this column'. You will then be prompted to enter the new column name. 

## Sorting data
You can sort data in OpenRefine by clicking on the drop-down menu for the column you want to sort on, and choosing `Sort`.

Once you have sorted the data, a new `Sort` drop-down menu will be displayed.

Unlike in Excel, 'Sorts' in OpenRefine are temporary - that is, if you remove the `Sort`, the data will go back to its original 'unordered' state. The 'Sort' drop-down menu lets you amend the existing sort (e.g., reverse the sort order), remove existing sorts, and/or make sorts permanent.

You can sort on multiple columns at the same time by adding another sorted column (in the same way).

> ## What is a word?
>
> Note here that depending on your dataset, an important setting is `Token Definition` under `Global Settings` (found in the top navbar). This defines what AntConc sees as a word, e.g. you need to specify that numbers, punctuation characters and symbols can be part of words in order for AntConc to see things like urls or other special characters that provide meaning (e.g. hashtags in tweets).
{: .callout}

>## Task 1: What % of all word tokens are accounted for by the 30 most common word types?
>* Use the `Word List` tab to count all word types and then use the output to make an estimate. Note: you may need to do some calculation outside of AntConc.
>
>>## Solution
>>
>>1. Remove any text from the search box, select `Sort by Freq` and hit `Start`.
>>2. Observe the figure of `1214917` word tokens. Select the frequency values of the 30 most common word types, paste them into a spreadsheet programme, and sum them. You should get `508791`. Use these two figures to calculate a percentage: `(508791/1214917) x 100 = 41.87%`
>>>* It is common in English language corpora to find that roughly half the corpus is accounted for by a small number of frequent words. This observation goes a long way to explaining way corpus linguists often present and work with lists of ‘top’ words (not that word lists are the only tool in the corpus linguists armoury, as we shall see!
>{: .solution}
{: .challenge}
