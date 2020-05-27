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

## Reordering columns
You can re-order the columns by clicking the drop-down menu at the top of the first column (labelled 'All'), and choosing `Edit columns->Re-order / remove columns …`.

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
